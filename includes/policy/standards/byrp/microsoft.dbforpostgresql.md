---
author: DCtheGeek
ms.service: azure-policy
ms.topic: include
ms.date: 01/08/2021
ms.author: dacoulte
ms.custom: generated
ms.openlocfilehash: d18352236116d28400eec5bbd91bbf3abb08f9eb
ms.sourcegitcommit: 8dd8d2caeb38236f79fe5bfc6909cb1a8b609f4a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98051694"
---
## <a name="azure-security-benchmark"></a>Azure セキュリティ ベンチマーク

[Azure セキュリティ ベンチマーク](../../../../articles/security/benchmarks/overview.md)には、Azure 上のクラウド ソリューションをセキュリティで保護する方法に関する推奨事項がまとめてあります。 このサービスを完全に Azure セキュリティ ベンチマークにマップする方法については、「[Azure Security Benchmark mapping files](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines)」 (Azure セキュリティ ベンチマークのマッピング ファイル) を参照してください。

すべての Azure サービスに対して使用可能な Azure Policy 組み込みを、このコンプライアンス基準に対応させる方法については、[Azure Policy の規制コンプライアンス - Azure セキュリティ ベンチマーク](../../../../articles/governance/policy/samples/azure-security-benchmark.md)に関するページを参照してください。

|Domain |コントロール ID |コントロールのタイトル |ポリシー<br /><sub>(Azure portal)</sub> |ポリシーのバージョン<br /><sub>(GitHub)</sub>  |
|---|---|---|---|---|
|ネットワークのセキュリティ |1.1 |Virtual Network でネットワーク セキュリティ グループまたは Azure Firewall を使用してリソースを保護する |[PostgreSQL サーバーに対してプライベート エンドポイントを有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F0564d078-92f5-4f97-8398-b9f58a51f70b) |[1.0.2](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnablePrivateEndPoint_Audit.json) |
|データ保護 |4.4. |転送中のすべての機密情報を暗号化する |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|データの復旧 |9.1 |定期的に自動バックアップを行う |[Azure Database for PostgreSQL の geo 冗長バックアップを有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F48af4db5-9b8b-401c-8e74-076be876a430) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/GeoRedundant_DBForPostgreSQL_Audit.json) |
|データの復旧 |9.2 |システムの完全バックアップを実行し、カスタマー マネージド キーをバックアップする |[Azure Database for PostgreSQL の geo 冗長バックアップを有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F48af4db5-9b8b-401c-8e74-076be876a430) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/GeoRedundant_DBForPostgreSQL_Audit.json) |

## <a name="cis-microsoft-azure-foundations-benchmark"></a>CIS Microsoft Azure Foundations Benchmark

すべての Azure サービスに対して使用可能な Azure Policy 組み込みを、このコンプライアンス基準に対応させる方法については、[Azure Policy の規制コンプライアンス - CIS Microsoft Azure Foundations Benchmark 1.1.0](../../../../articles/governance/policy/samples/cis-azure-1-1-0.md) に関するページを参照してください。
このコンプライアンス標準の詳細については、[CIS Microsoft Azure Foundations Benchmark](https://www.cisecurity.org/benchmark/azure/) に関するページを参照してください。

|Domain |コントロール ID |コントロールのタイトル |ポリシー<br /><sub>(Azure portal)</sub> |ポリシーのバージョン<br /><sub>(GitHub)</sub>  |
|---|---|---|---|---|
|データベース サービス |4.12 |サーバー パラメーターである "log_checkpoints" が PostgreSQL データベース サーバー向けに [オン] に設定されていることを確認する |[PostgreSQL データベース サーバーではログ チェックポイントが有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Feb6f77b9-bd53-4e35-a23d-7f65d5f0e43d) |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableLogCheckpoint_Audit.json) |
|データベース サービス |4.13 |PostgreSQL データベース サーバーで [SSL 接続を強制する] が [有効] に設定されていることを確認する |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|データベース サービス |4.14 |サーバー パラメーターである "log_connections" が PostgreSQL データベース サーバー向けに [オン] に設定されていることを確認する |[PostgreSQL データベース サーバーではログ接続が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Feb6f77b9-bd53-4e35-a23d-7f65d5f0e442) |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableLogConnections_Audit.json) |
|データベース サービス |4.15 |サーバー パラメーターである "log_disconnections" が PostgreSQL データベース サーバー向けに [オン] に設定されていることを確認する |[PostgreSQL データベース サーバーの切断はログに記録する必要がある。](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Feb6f77b9-bd53-4e35-a23d-7f65d5f0e446) |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableLogDisconnections_Audit.json) |
|データベース サービス |4.17 |サーバー パラメーターである "connection_throttling" が PostgreSQL データベース サーバー向けに [オン] に設定されていることを確認する |[PostgreSQL データベース サーバーでは接続の調整が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F5345bb39-67dc-4960-a1bf-427e16b9a0bd) |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_ConnectionThrottling_Enabled_Audit.json) |

## <a name="hipaa-hitrust-92"></a>HIPAA HITRUST 9.2

すべての Azure サービスに対して使用可能な Azure Policy 組み込みがこのコンプライアンス標準にどのように対応するのかを確認するには、[Azure Policy の規制コンプライアンス - HIPAA HITRUST 9.2](../../../../articles/governance/policy/samples/hipaa-hitrust-9-2.md) に関するページを参照してください。
このコンプライアンス標準の詳細については、[HIPAA HITRUST 9.2](https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html) に関するページを参照してください。

|Domain |コントロール ID |コントロールのタイトル |ポリシー<br /><sub>(Azure portal)</sub> |ポリシーのバージョン<br /><sub>(GitHub)</sub>  |
|---|---|---|---|---|
|ネットワーク接続コントロール |0809.01n2Organizational.1234 - 01.n |ネットワーク トラフィックは、ファイアウォールと、各ネットワーク アクセス ポイントまたは外部通信サービスのマネージド インターフェイスに対するその他のネットワーク関連の制限を介し、組織のアクセス制御ポリシーに従って制御されます。 |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|ネットワーク接続コントロール |0810.01n2Organizational.5 - 01.n |送信される情報はセキュリティで保護され、少なくとも、オープンな公衆ネットワークでは暗号化されます。 |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|ネットワーク接続コントロール |0811.01n2Organizational.6 - 01.n |トラフィック フロー ポリシーの例外は、サポートしているミッションとビジネス ニーズおよび例外の期間と共に文書化され、少なくとも年に 1 回確認されます。トラフィック フロー ポリシーの例外は、明示的なミッションとビジネス ニーズによってサポートされなくなった時点で削除されます。 |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|ネットワーク接続コントロール |0812.01n2Organizational.8 - 01.n |リモート以外の接続を確立するリモート デバイスは、外部 (リモート) リソースと通信することを許可されません。 |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|ネットワーク接続コントロール |0814.01n1Organizational.12 - 01.n |ユーザーが内部ネットワークに接続できるかどうかは、アクセス制御ポリシーと、臨床およびビジネス アプリケーションの要件に従って、マネージド インターフェイスで、"既定で拒否、例外で許可" ポリシーを使用して制限されます。 |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|外部パーティに関連するリスクの特定 |1450.05i2Organizational.2 - 05.i |組織は、年間レビューを実行することで、情報サプライ チェーン全体に適切な情報セキュリティが存在することについて、満足できる保証を得ます。これには、情報サプライ チェーンが依存しているすべてのパートナーとサードパーティ プロバイダーが含まれます。 |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |
|バックアップ |1618.09l1Organizational.45 - 09.l |プライマリ サイトでのデータの破損から適切に保護されるのに十分な距離だけ離れた物理的に安全な場所にバックアップを保管し、適切な物理的および環境的な制御を適用して、リモートの場所で確実に保護します。 |[Azure Database for PostgreSQL の geo 冗長バックアップを有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F48af4db5-9b8b-401c-8e74-076be876a430) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/GeoRedundant_DBForPostgreSQL_Audit.json) |
|バックアップ |1623.09l2Organizational.4 - 09.l |機密性を保証するため、対象となる情報を暗号化された形式でバックアップします。 |[Azure Database for PostgreSQL の geo 冗長バックアップを有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F48af4db5-9b8b-401c-8e74-076be876a430) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/GeoRedundant_DBForPostgreSQL_Audit.json) |
|バックアップ |1626.09l3Organizational.5 - 09.l |組織は、対象となる情報の現在の取得可能なコピーが利用可能であることを、サーバーを移動する前確認します。 |[Azure Database for PostgreSQL の geo 冗長バックアップを有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F48af4db5-9b8b-401c-8e74-076be876a430) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/GeoRedundant_DBForPostgreSQL_Audit.json) |
|オンライン トランザクション |0947.09y2Organizational.2 - 09.y |組織では、トランザクションの詳細のストレージがパブリックにアクセスできる環境の外部に配置され (たとえば、組織のイントラネット上に存在するストレージ プラットフォーム上)、インターネットから直接アクセスできるストレージ メディアで保持および公開されないようにします。 |[PostgreSQL データベース サーバーでは [SSL 接続を強制する] が有効でなければならない](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fd158790f-bfb0-486c-8631-2dc6b4e8e6af) |[1.0.1](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/SQL/PostgreSQL_EnableSSL_Audit.json) |

