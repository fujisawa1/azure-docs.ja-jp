---
title: Azure API for FHIR で診断ログを有効にする
description: この記事では、Azure API for FHIR® で診断ログを有効にする方法について説明します。
services: healthcare-apis
ms.service: healthcare-apis
ms.subservice: fhir
ms.topic: conceptual
ms.reviewer: dseven
ms.author: cavoeg
author: CaitlinV39
ms.date: 11/01/2019
ms.openlocfilehash: 54119585d4f1377b60b85fbad01fe90f097a304f
ms.sourcegitcommit: a43a59e44c14d349d597c3d2fd2bc779989c71d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "95905176"
---
# <a name="enable-diagnostic-logging-in-azure-api-for-fhir"></a>Azure API for FHIR で診断ログを有効にする

この記事では、Azure API for FHIR で診断ログを有効にし、それらのログのサンプル クエリを確認できるようにする方法について説明します。 診断ログへのアクセスは、規制要件 (HIPAA など) への準拠が必須であるすべての医療サービスにとって不可欠です。 診断ログを有効にする Azure API for FHIR の機能は、Azure portal の [**診断設定**](../azure-monitor/platform/diagnostic-settings.md)です。 

## <a name="enable-audit-logs"></a>監査ログを有効にする
1. Azure API for FHIR で診断ログを有効にするには、Azure portal でお使いの Azure API for FHIR サービスを選択します 
2. **[診断設定]** に移動します。 
![診断設定](media/diagnostic-logging/diagnostic-settings-screen.png) 

3. **[+ 診断設定を追加する]** を選択します

4. 設定の名前を入力します。

5. 診断ログへのアクセスに使用する方法を選択します。

    1. 監査や手動での検査のために、**ストレージ アカウントにアーカイブ** します。 使用するストレージ アカウントは既に作成済みである必要があります。
    2. サード パーティのサービスやカスタム分析ソリューションで取り込むために、**イベント ハブにストリーム配信** します。 この手順を構成する前に、イベント ハブの名前空間とイベント ハブのポリシーを作成する必要があります。
    3. Azure Monitor の **Log Analytics ワークスペースにストリーム配信** します。 このオプションを選択する前に、Log Analytics ワークスペースを作成する必要があります。

6. **AuditLogs** と、キャプチャするすべてのメトリックを選択します。 Azure IoT Connector for FHIR を使用している場合は、メトリックの **[エラー]、[トラフィック]、[待機時間]** を必ず選択してください。 

   :::image type="content" source="media/iot-metrics-export/diagnostic-setting-add.png" alt-text="IoT Connector2" lightbox="media/iot-metrics-export/diagnostic-setting-add.png":::

7. **[保存]** を選びます。


> [!Note] 
> 最初のログが Log Analytics に表示されるまでには、最大で 15 分かかることがあります。  
 
診断ログの使用方法の詳細については、[Azure リソース ログのドキュメント](../azure-monitor/platform/platform-logs-overview.md)を参照してください。

## <a name="audit-log-details"></a>監査ログの詳細
現時点では、Azure API for FHIR サービスは、監査ログで次のフィールドを返します。 

|フィールド名  |Type  |Notes  |
|---------|---------|---------|
|CallerIdentity|動的|ID 情報を含む汎用プロパティ バッグ
|CallerIdentityIssuer|String|発行者 
|CallerIdentityObjectId|String|Object_Id 
|CallerIPAddress|String|呼び出し元の IP アドレス 
|CorrelationId|String| 関連付け ID
|FhirResourceType|String|操作が実行されたリソースの種類
|LogCategory|String|ログのカテゴリ (現在、‘AuditLogs’ LogCategory を返しています)
|Location|String|要求を処理したサーバーの場所 (例: 米国中南部)
|OperationDuration|int|この要求の完了にかかった時間 (秒)
|OperationName|String| 操作の種類 (update、search-type など) を記述します
|RequestUri|String|要求 URI 
|ResultType|String|現在使用可能な値は、**Started**、**Succeeded**、または **Failed**
|StatusCode|int|HTTP 状態コード。 (例: 200) 
|TimeGenerated|DateTime|イベントの日付と時刻|
|Properties|String| fhirResourceType のプロパティを記述します
|SourceSystem|String| ソース システム (この場合、常に Azure)
|TenantId|String|テナント ID
|Type|String|ログの種類 (この場合、常に MicrosoftHealthcareApisAuditLog)
|_ResourceId|String|リソースの詳細

## <a name="sample-queries"></a>サンプル クエリ

ログ データを調査するために使用できるいくつかの基本的な Application Insights クエリを次に示します。

**最新の 100 件** のログを表示するには、次のクエリを実行します。

```Application Insights
MicrosoftHealthcareApisAuditLogs
| limit 100
```

**FHIR のリソースの種類** で操作をグループ化するには、次のクエリを実行します。

```Application Insights
MicrosoftHealthcareApisAuditLogs 
| summarize count() by FhirResourceType
```

すべての **失敗した結果** を取得するには、次のクエリを実行します。

```Application Insights
MicrosoftHealthcareApisAuditLogs 
| where ResultType == "Failed" 
```

## <a name="conclusion"></a>まとめ 
診断ログにアクセスできることは、サービスを監視し、コンプライアンス レポートを提供するために不可欠です。 Azure API for FHIR を使用すると、診断ログを使用してこれらのアクションを実行できます。 
 
FHIR は HL7 の登録商標であり、HL7 の許可を得て使用しています。

## <a name="next-steps"></a>次のステップ
この記事では、Azure API for FHIR の監査ログを有効にする方法について説明しました。 次に、Azure API for FHIR で構成できるその他の追加設定について説明します。
 
>[!div class="nextstepaction"]
>[[追加設定]](azure-api-for-fhir-additional-settings.md)
