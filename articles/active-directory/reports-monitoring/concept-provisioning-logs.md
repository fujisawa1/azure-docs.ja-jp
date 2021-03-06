---
title: Azure Active Directory ポータルのプロビジョニング ログ (プレビュー) | Microsoft Docs
description: Azure Active Directory ポータルのプロビジョニング ログ レポートの概要
services: active-directory
documentationcenter: ''
author: MarkusVi
manager: daveba
editor: ''
ms.assetid: 4b18127b-d1d0-4bdc-8f9c-6a4c991c5f75
ms.service: active-directory
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: identity
ms.subservice: report-monitor
ms.date: 1/19/2021
ms.author: markvi
ms.reviewer: arvinh
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05a514debcf8036a296bbe66b2dd75c7dacacdc2
ms.sourcegitcommit: fc401c220eaa40f6b3c8344db84b801aa9ff7185
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98600753"
---
# <a name="provisioning-reports-in-the-azure-active-directory-portal-preview"></a>Azure Active Directory ポータルのプロビジョニング レポート (プレビュー)

Azure Active Directory (Azure AD) のレポート アーキテクチャは、次のコンポーネントで構成されます。

- **アクティビティ** 
    - **サインイン** – マネージド アプリケーションの使用状況とユーザー サインイン アクティビティに関する情報。
    - **監査ログ** - [監査ログ](concept-audit-logs.md)は、ユーザーとグループの管理や、マネージド アプリケーションとディレクトリのアクティビティに関するシステム アクティビティ情報を提供します。
    - **プロビジョニング ログ** - Azure AD プロビジョニング サービスによってプロビジョニングされたユーザー、グループ、およびロールに関するシステム アクティビティを提供します。 

- **Security** 
    - **リスクの高いサインイン** - [リスクの高いサインイン](../identity-protection/overview-identity-protection.md)は、ユーザー アカウントの正当な所有者ではない人によって行われた可能性があるサインイン試行の指標です。
    - **リスクのフラグ付きユーザー** - [リスクの高いユーザー](../identity-protection/overview-identity-protection.md)は、侵害された可能性があるユーザー アカウントの指標です。

このトピックでは、プロビジョニング レポートの概要を説明します。

## <a name="prerequisites"></a>前提条件

### <a name="who-can-access-the-data"></a>誰がデータにアクセスできますか。
* アプリケーションの所有者は、自分が所有するアプリケーションのログを表示できます
* セキュリティ管理者、セキュリティ閲覧者、レポート閲覧者、アプリケーション管理者、クラウド アプリケーション管理者のいずれかのロールであるユーザー
* [provisioningLogs アクセス許可](https://docs.microsoft.com/azure/active-directory/roles/custom-enterprise-app-permissions#full-list-of-permissions)を持つカスタム ロールのユーザー
* グローバル管理者


### <a name="what-azure-ad-license-do-you-need-to-access-provisioning-activities"></a>プロビジョニング アクティビティにアクセスするために必要な Azure AD ライセンス

すべてのプロビジョニング アクティビティ レポートを閲覧するためには、ご利用のテナントに、Azure AD Premium ライセンスが関連付けられている必要があります。 Azure Active Directory エディションにアップグレードするには、「[Azure Active Directory Premium の概要](../fundamentals/active-directory-get-started-premium.md)」を参照してください。 

## <a name="provisioning-logs"></a>プロビジョニング ログ

プロビジョニング ログから、次の情報を得ることができます。

* ServiceNow で正常に作成されたグループ
* Adobe から正常に削除されたユーザー
* DropBox で作成に失敗したユーザー

[Azure portal](https://portal.azure.com) の **[Azure Active Directory]** ブレードの **[監視]** セクションで **[プロビジョニング ログ]** を選択して、プロビジョニング レポートにアクセスできます。 プロビジョニング レコードによっては、ポータルに表示されるまでに最大 2 時間かかるものもあります。

![プロビジョニング ログ](./media/concept-provisioning-logs/access-provisioning-logs.png "プロビジョニング ログ")


プロビジョニング ログには、次のものを示す既定のリスト ビューがあります。

- ID
- アクション
- ソース システム
- ターゲット システム
- 状態
- 日付


![既定の列](./media/concept-provisioning-logs/default-columns.png "既定の列")

リスト ビューをカスタマイズするには、ツール バーの **[列]** をクリックします。

![列の選択](./media/concept-provisioning-logs/column-chooser.png "列の選択")

これで、追加のフィールドの表示または既に表示されているフィールドの削除ができます。

![使用可能な列](./media/concept-provisioning-logs/available-columns.png "使用可能な列")

詳細な情報を取得するには、リスト ビューで項目を選択します。

![詳細情報](./media/concept-provisioning-logs/steps.png "Assert")


## <a name="filter-provisioning-activities"></a>プロビジョニング アクティビティのフィルター処理

プロビジョニング データをフィルター処理できます。 いくつかのフィルター値は、テナントに基づいて動的に設定されます。 たとえば、テナントに作成イベントがない場合は、作成のフィルター オプションはありません。
既定のビューでは、次のフィルターを選択できます。

- ID
- Date
- Status
- アクション


![フィルターの追加](./media/concept-provisioning-logs/default-filter.png "Assert")

**ID** フィルターを使用すると、関心のある名前または ID を指定できます。 この ID には、ユーザー、グループ、ロール、またはその他のオブジェクトを指定できます。 オブジェクトの名前または ID で検索できます。 ID はシナリオによって異なります。 たとえば、Azure AD から SalesForce にオブジェクトをプロビジョニングする場合、ソース ID は Azure AD 内のユーザーのオブジェクト ID であり、ターゲット ID は Salesforce のユーザーの ID です。 Workday から Active Directory にプロビジョニングする場合、ソース ID は Workday ワーカーの従業員 ID です。 ユーザーの名前が必ずしも ID 列に存在するとは限らないことに注意してください。 常に 1 つの ID が存在します。 


**[日付]** フィルターでは、返されるデータの期間を定義できます。  
次のいずれかの値になります。

- 1 か月
- 7 日
- 30 日
- 24 時間
- カスタム期間

カスタムの期間を選択すると、開始日と終了日を構成できます。


**[状態]** フィルターでは、次のいずれかを選択できます。

- All
- Success
- 障害
- スキップ



**[アクション]** フィルターでは、次のものをフィルター処理できます。

- 作成 
- 更新
- 削除
- Disable
- その他

既定のビューのフィルターに加えて、次のフィルターを設定することもできます。

- [ジョブ ID]
- サイクル ID
- 変更 ID
- ソース ID
- ターゲット ID
- Application


![フィールドを選択する](./media/concept-provisioning-logs/add-filter.png "フィールドを選択する")


- **[ジョブ ID]** - プロビジョニングを有効にした各アプリケーションに、一意のジョブ ID が関連付けられます。   

- **[サイクル ID]** - プロビジョニング サイクルを一意に識別します。 この ID をサポートと共有して、このイベントが発生したサイクルを調べることができます。

- **[変更 ID]** - プロビジョニング イベントの一意の識別子。 この ID をサポートと共有して、プロビジョニング イベントを検索できます。   


- **[ソース システム]** - ID のプロビジョニング元となる場所を指定できます。 たとえば、Azure AD から ServiceNow にオブジェクトをプロビジョニングする場合、ソース システムは Azure AD です。 

- **[ターゲット システム]** - ID のプロビジョニング先となる場所を指定できます。 たとえば、Azure AD から ServiceNow にオブジェクトをプロビジョニングする場合、ターゲット システムは ServiceNow です。 

- **アプリケーション** - 特定の文字列が含まれている表示名を持つアプリケーションのレコードのみを表示できます。

 

## <a name="provisioning-details"></a>プロビジョニングの詳細 

プロビジョニング リスト ビューで項目を選択すると、この項目の詳細が表示されます。
詳細は、次のカテゴリに基づいてグループ化されます。

- 手順

- トラブルシューティングと推奨事項

- 変更されたプロパティ

- まとめ


![プロビジョニングの詳細](./media/concept-provisioning-logs/provisioning-tabs.png "タブ")



### <a name="steps"></a>手順

**[ステップ]** タブには、オブジェクトをプロビジョニングするために実行される手順の概要が示されます。 オブジェクトのプロビジョニングは次の 4 つの手順で構成されます。 

- オブジェクトをインポートする
- オブジェクトがスコープ内にあるかどうかを判断する
- ソースとターゲットの間でオブジェクトを一致させる
- オブジェクトをプロビジョニングする (アクションの実行 - 作成、更新、削除、または無効化)



![プロビジョニングの手順を示す [ステップ] タブを示すスクリーンショット。](./media/concept-provisioning-logs/steps.png "Assert")


### <a name="troubleshoot-and-recommendations"></a>トラブルシューティングと推奨事項


**[トラブルシューティングと推奨事項]** タブには、エラー コードと理由が表示されます。 エラー情報は、エラーが発生した場合にのみ提供されます。 


### <a name="modified-properties"></a>変更されたプロパティ

**[変更されたプロパティ]** には、古い値と新しい値が表示されます。 古い値が存在しない場合、古い値の列は空白になります。 


### <a name="summary"></a>まとめ

**[概要]** タブには、ソース システムとターゲット システムのオブジェクトの発生内容の概要と識別子が表示されます。 

## <a name="what-you-should-know"></a>知っておくべきこと

- 報告されたプロビジョニング データは、Premium Edition の場合は 30 日間、Free Edition の場合は 7 日間、Azure portal に保存されます。プロビジョニング ログは[ログ分析](../app-provisioning/application-provisioning-log-analytics.md)のために発行して、30 日間を超えても保存することができます。 

- [変更 ID] 属性は、一意の識別子として使用できます。 これは、たとえば製品サポートとやり取りするときに便利です。

- ユーザーがスコープに含まれていない場合、スキップされたイベントが表示されることがあります。 同期スコープがすべてのユーザーとグループに設定されているときは特にこれが予想されます。 Microsoft のサービスでは、スコープ外であっても、テナント内のすべてのオブジェクトが評価されます。 

- プロビジョニング ログは現在、政府のクラウドで利用できません。 プロビジョニング ログにアクセスできない場合は、一時的な回避策として監査ログを使用してください。 

- プロビジョニング ログには、ロールのインポートは表示されません (AWS、SalesForce、ZenDesk に適用されます)。 ロールのインポートのログは、監査ログで確認できます。 

## <a name="error-codes"></a>エラー コード

次の表を利用し、プロビジョニング ログに記録されていることがあるエラーの解決方法をより深く理解してください。 記載されていないエラー コードがあった場合は、このページの下部にあるリンクを使用してフィードバックを提供してください。 

|エラー コード|説明|
|---|---|
|Conflict、EntryConflict|Azure AD またはアプリケーションで、競合している属性値を修正します。または、競合しているユーザー アカウントが一致し、取って代わられたと思われるかどうか、一致する属性の構成を確認します。 一致する属性の構成の詳細については、次の[ドキュメント](../app-provisioning/customize-application-attributes.md)を確認してください。|
|TooManyRequests|ターゲット アプリは過負荷になり多すぎる要求を受け取っているため、ユーザーを更新するこの試行を拒否しました。 することはありません。 この試行は自動的に中止されます。 Microsoft もこの問題について通知されています。|
|InternalServerError |ターゲット アプリから予期しないエラーが返されました。 ターゲット アプリケーションに、その動作を妨げているサービスの問題がある可能性があります。 この試行は 40 分で自動的に中止されます。|
|InsufficientRights、MethodNotAllowed、NotPermitted、Unauthorized| Azure AD はターゲット アプリケーションによって認証できましたが、更新を実行する権限がありませんでした。 ターゲット アプリケーションによって提供された手順と、それぞれのアプリケーションの[チュートリアル](../saas-apps/tutorial-list.md)を確認してください。|
|UnprocessableEntity|ターゲット アプリケーションが予期しない応答を返しました。 ターゲット アプリケーションの構成が正しくないか、ターゲット アプリケーションに、その動作を妨げているサービスの問題がある可能性があります。|
|WebExceptionProtocolError |ターゲット アプリケーションへの接続中に HTTP プロトコル エラーが発生しました。 することはありません。 この試行は 40 分で自動的に中止されます。|
|InvalidAnchor|プロビジョニング サービスによって以前作成または照合されたユーザーは存在しなくなりました。 そのユーザーが存在することを確認してください。 すべてのユーザーを強制的に再照合するには、MS Graph API を使用して[ジョブを再開](/graph/api/synchronization-synchronizationjob-restart?tabs=http&view=graph-rest-beta)します。 プロビジョニングを再開すると初期サイクルがトリガーされ、完了するまで時間がかかる場合があることに注意してください。 また、プロビジョニング サービスが操作に使用するキャッシュが削除されます。これは、テナント内のすべてのユーザーとグループが再度評価される必要があり、特定のプロビジョニング イベントが削除される可能性があることを意味します。|
|NotImplemented | ターゲット アプリから予期しない応答が返されました。 アプリの構成が正しくないか、ターゲット アプリに、その動作を妨げているサービスの問題がある可能性があります。 ターゲット アプリケーションによって提供された手順と、それぞれのアプリケーションの[チュートリアル](../saas-apps/tutorial-list.md)を確認してください。 |
|MandatoryFieldsMissing、MissingValues |必須の値がないため、ユーザーを作成できませんでした。 ソース レコード内の不足している属性値を修正するか、一致する属性の構成を調べて、必須フィールドが省略されていないことを確認します。 一致する属性の構成に関する[詳細を確認](../app-provisioning/customize-application-attributes.md)してください。|
|SchemaAttributeNotFound |ターゲット アプリケーションに存在しない属性が指定されたため、操作を実行できませんでした。 属性のカスタマイズに関する[ドキュメント](../app-provisioning/customize-application-attributes.md)を参照し、構成が正しいことを確認してください。|
|InternalError |Azure AD プロビジョニング サービス内で内部サービス エラーが発生しました。 することはありません。 この試行は 40 分で自動的に再試行されます。|
|InvalidDomain |無効なドメイン名を含む属性値が原因で操作を実行できませんでした。 ユーザーのドメイン名を更新するか、ターゲット アプリケーションの許可リストにそのドメイン名を追加します。 |
|タイムアウト |ターゲット アプリケーションが応答するのに時間がかかりすぎたため、操作を完了できませんでした。 することはありません。 この試行は 40 分で自動的に再試行されます。|
|LicenseLimitExceeded|このユーザーが使用できるライセンスがないため、ターゲット アプリケーションでユーザーを作成できませんでした。 ターゲット アプリケーションの追加ライセンスを購入するか、ユーザーの割り当てと属性マッピングの構成を調べて、正しい属性で正しいユーザーが割り当てられていることを確認します。|
|DuplicateTargetEntries  |ターゲット アプリケーションの複数のユーザーに、構成済みの一致する属性があると検出されたため、操作を完了できませんでした。 重複しているユーザーをターゲット アプリケーションから削除するか、[ここ](../app-provisioning/customize-application-attributes.md)で説明されているように、属性マッピングを再構成します。|
|DuplicateSourceEntries | 複数のユーザーに、構成済みの一致する属性があると検出されたため、操作を完了できませんでした。 重複しているユーザーを削除するか、[ここ](../app-provisioning/customize-application-attributes.md)で説明されているように、属性マッピングを再構成します。|
|ImportSkipped | 各ユーザーを評価するときに、ソース システムからユーザーをインポートするよう試みます。 このエラーが発生するのは一般的に、インポートするユーザーが、属性マッピングで定義されている一致するプロパティを持っていない場合です。 一致する属性のユーザー オブジェクトに値が指定されていない場合、スコープ、一致、またはエクスポートの変更を評価することはできません。 このエラーが発生したとしても、このユーザーのスコープがまだ評価されていないため、ユーザがスコープ内にあることを示すものではないことに注意してください。|
|EntrySynchronizationSkipped | プロビジョニング サービスによってソース システムに対するクエリが正常に実行され、ユーザーが識別されました。 ユーザーに対してこれ以上の操作は行われず、スキップされました。 スキップの原因としては、ユーザーがスコープ外にあるか、ユーザーがターゲット システムに既に存在していて、それ以上の変更は必要ないためです。|
|SystemForCrossDomainIdentityManagementMultipleEntriesInResponse| GET 要求を実行してユーザーまたはグループを取得すると、複数のユーザーまたはグループが応答で受信されました。 応答で受信すると想定していたユーザーまたはグループは 1 つだけです。 [たとえば](../app-provisioning/use-scim-to-provision-users-and-groups.md#get-group)、グループを取得するための GET 要求を実行してメンバーを除外するフィルターを指定したときに、SCIM エンドポイントがメンバーを返した場合、このエラーがスローされます。|

## <a name="next-steps"></a>次のステップ

* [ユーザー プロビジョニングの状態を確認する](../app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user.md)
* [Azure AD ギャラリー アプリケーションへのユーザー プロビジョニングの構成に関する問題](../app-provisioning/application-provisioning-config-problem.md)
* [プロビジョニング ログ グラフ API](/graph/api/resources/provisioningobjectsummary?view=graph-rest-beta)
