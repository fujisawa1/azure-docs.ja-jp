---
title: クイック スタート:Azure Key Vault 証明書の設定と表示 - Azure CLI
description: Azure CLI を使用して Azure Key Vault との間で証明書の設定と取得を行う方法を紹介したクイックスタート
services: key-vault
author: msmbaldwin
manager: rkarlin
tags: azure-resource-manager
ms.service: key-vault
ms.subservice: certificates
ms.topic: quickstart
ms.custom: mvc, seo-javascript-september2019, seo-javascript-october2019, devx-track-azurecli
ms.date: 09/03/2019
ms.author: mbaldwin
ms.openlocfilehash: 2bb718d038dd7b3f5aa6f3bac1ce1de572c8e829
ms.sourcegitcommit: 2aa52d30e7b733616d6d92633436e499fbe8b069
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97936364"
---
# <a name="quickstart-set-and-retrieve-a-certificate-from-azure-key-vault-using-azure-cli"></a>クイック スタート:Azure CLI を使用して Azure Key Vault から証明書の設定と取得を行う

このクイックスタートでは、Azure CLI を使用して Azure Key Vault にキー コンテナーを作成します。 Azure Key Vault は、セキュリティで保護されたシークレット ストアとして機能するクラウド サービスです。 キー、パスワード、証明書、およびその他のシークレットを安全に保管することができます。 Key Vault の詳細については、[概要](../general/overview.md)に関するページを参照してください。 Azure CLI は、コマンドまたはスクリプトを使用して Azure リソースを作成および管理するために使用します。 この作業を完了したら、証明書を格納します。

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [azure-cli-prepare-your-environment.md](../../../includes/azure-cli-prepare-your-environment.md)]

 - このクイックスタートには、Azure CLI のバージョン 2.0.4 以降が必要です。 Azure Cloud Shell を使用している場合は、最新バージョンが既にインストールされています。

## <a name="create-a-resource-group"></a>リソース グループを作成する

リソース グループとは、Azure リソースのデプロイと管理に使用する論理コンテナーです。 次の例では、*ContosoResourceGroup* という名前のリソース グループを *eastus* の場所に作成します。

```azurecli
az group create --name "ContosoResourceGroup" --location eastus
```

## <a name="create-a-key-vault"></a>Key Vault の作成

次に、前の手順で作成したリソース グループに Key Vault を作成します。 いくつかの情報を指定する必要があります。

- このクイック スタートでは、**Contoso-vault2** を使用します。 テストでは一意の名前を指定する必要があります。
- リソース グループ名: **ContosoResourceGroup**
- 場所: **米国東部**

```azurecli
az keyvault create --name "Contoso-Vault2" --resource-group "ContosoResourceGroup" --location eastus
```

このコマンドレットの出力では、新しく作成したキー コンテナーのプロパティが示されます。 次の 2 つのプロパティをメモしておきます。

- **Vault Name**:この例では、これは **Contoso-Vault2** です。 この名前を他の Key Vault コマンドに使用できます。
- **Vault URI (コンテナー URI)** :この例では、これは https://contoso-vault2.vault.azure.net/ です。 その REST API から資格情報コンテナーを使用するアプリケーションは、この URI を使用する必要があります。

この時点で、自分の Azure アカウントが唯一、この新しいコンテナーで任意の操作を実行することを許可されています。

## <a name="add-a-certificate-to-key-vault"></a>証明書を Key Vault に追加する

証明書をコンテナーに追加するには、いくつかの追加の手順を実行する必要があります。 この証明書は、アプリケーションによって使用される可能性があります。 

次のコマンドを入力して、**ExampleCertificate** という既定のポリシーを含む自己署名証明書を作成します。

```azurecli
az keyvault certificate create --vault-name "Contoso-Vault2" -n ExampleCertificate -p "$(az keyvault certificate get-default-policy)"
```

これで、URI を使用して、Azure Key Vault に追加したこの証明書を参照できるようになりました。 **"https://Contoso-Vault2.vault.azure.net/certificates/ExampleCertificate"** を使用して、現在のバージョンを取得します。 

以前に格納した証明書を表示するには:

```azurecli

az keyvault certificate show --name "ExampleCertificate" --vault-name "Contoso-Vault2"
```

これで、キー コンテナーを作成し、証明書を格納した後、取得しました。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このコレクションの他のクイックスタートとチュートリアルは、このクイックスタートに基づいています。 後続のクイック スタートおよびチュートリアルを引き続き実行する場合は、これらのリソースをそのまま残しておくことをお勧めします。
必要がなくなったら、[az group delete](/cli/azure/group) コマンドを使用して、リソース グループおよびすべての関連リソースを削除できます。 次のように、リソースを削除できます。

```azurecli
az group delete --name ContosoResourceGroup
```

## <a name="next-steps"></a>次のステップ

このクイックスタートでは、キー コンテナーを作成して証明書を格納しました。 Key Vault およびアプリケーションとの統合方法の詳細については、引き続き以下の記事を参照してください。

- [Azure Key Vault の概要](../general/overview.md)を確認する
- [Azure CLI az keyvault コマンド](/cli/azure/keyvault?view=azure-cli-latest)のリファレンスを参照する
- [Key Vault のセキュリティの概要](../general/security-overview.md)を確認する
