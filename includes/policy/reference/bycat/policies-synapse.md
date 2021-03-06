---
author: DCtheGeek
ms.service: azure-policy
ms.topic: include
ms.date: 01/08/2021
ms.author: dacoulte
ms.custom: generated
ms.openlocfilehash: a0751e7e4c90f04cd5e28610e2c62dbec6a7adcf
ms.sourcegitcommit: 8dd8d2caeb38236f79fe5bfc6909cb1a8b609f4a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98047736"
---
|名前<br /><sub>(Azure portal)</sub> |説明 |効果 |Version<br /><sub>(GitHub)</sub> |
|---|---|---|---|
|[Azure Synapse ワークスペースでは保存データを暗号化するためにカスタマー マネージド キーを使用する必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Ff7d52b2d-e161-4dfa-a82b-55e564167385) |カスタマー マネージド キーを使用して、Azure Synapse ワークスペースに格納されているデータの保存時の暗号化を制御します。 カスタマー マネージド キーを使用すると、サービス マネージド キーで実行される既定の暗号化レイヤーの上に 2 番目の暗号化レイヤーが追加されて、二重の暗号化が提供されます。 |Audit、Deny、Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Synapse/SynapseWorkspaceCMK_Audit.json) |
|[Azure Synapse ワークスペースの IP ファイアウォール規則を削除する必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F56fd377d-098c-4f02-8406-81eb055902b8) |IP ファイアウォール規則をすべて削除すると、Azure Synapse ワークスペースへのアクセス手段がプライベート エンドポイントに限定され、セキュリティが向上します。 ワークスペースのパブリック ネットワーク アクセスを許可するファイアウォール規則の作成が、この構成によって監査されます。 |Audit、Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Synapse/SynapseWorkspaceFirewallRules_Audit.json) |
|[Azure Synapse ワークスペースでマネージド ワークスペース仮想ネットワークを有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F2d9dbfa3-927b-4cf0-9d0f-08747f971650) |マネージド ワークスペース仮想ネットワークを有効にすることで、そのワークスペースが他のワークスペースから分離されたネットワークであることが保証されます。 また、この仮想ネットワークにデプロイされる Spark リソースとデータ統合によって、Spark のアクティビティに関してユーザー レベルの分離が確保されます。 |Audit、Deny、Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Synapse/SynapseWorkspaceManagedVnet_Audit.json) |
|[Azure Synapse ワークスペースのプライベート エンドポイント接続を有効にする必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F72d11df1-dd8a-41f7-8925-b05b960ebafc) |プライベート エンドポイントを構成することで、Azure Synapse ワークスペースに対してプライベートに接続することができます。 これは、Azure Synapse ワークスペースへの安全な通信チャネルを確保する目的で使用されます。 |Audit、Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Synapse/SynapseWorkspaceUsePrivateLinks_Audit.json) |
|[Synapse マネージド プライベート エンドポイントの接続は、承認された Azure Active Directory テナントのリソースに限定する必要がある](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F3a003702-13d2-4679-941b-937e58c443f0) |承認された Azure Active Directory (Azure AD) テナント内のリソースへの接続のみを許可することによって、Synapse ワークスペースを保護します。 Azure AD テナントの承認は、ポリシーの割り当て時に定義できます。 |Audit, Disabled, Deny |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Synapse/Workspace_DataExfiltrationPrevention_Deny.json) |
