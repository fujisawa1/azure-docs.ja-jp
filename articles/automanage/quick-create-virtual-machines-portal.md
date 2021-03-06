---
title: クイックスタート - Azure portal で VM に対して Azure Automanage を有効にする
description: Azure portal で新規または既存の VM 上の仮想マシンに対して Automanage を迅速に有効にする方法について説明します。
author: ju-shim
ms.service: virtual-machines
ms.subservice: automanage
ms.workload: infrastructure
ms.topic: quickstart
ms.date: 09/04/2020
ms.author: jushiman
ms.openlocfilehash: 69f43b626bb50171ceaca1b7a8761bec040d1dd6
ms.sourcegitcommit: 4064234b1b4be79c411ef677569f29ae73e78731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92897230"
---
# <a name="quickstart-enable-azure-automanage-for-virtual-machines-in-the-azure-portal"></a>クイック スタート:Azure portal で仮想マシンに対して Azure Automanage を有効にする

Azure portal を使用して新規または既存の仮想マシンで自動管理を有効にすることにより、仮想マシンに対して Azure Automanage の使用を開始します。


## <a name="prerequisites"></a>前提条件

Azure サブスクリプションをお持ちでない場合は、始める前に[アカウントを作成](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)してください。

> [!NOTE]
> 無料試用版アカウントでは、このチュートリアルで使用されている仮想マシンを利用できません。 従量課金制サブスクリプションにアップグレードしてください。

> [!IMPORTANT]
> 既存の Automanage アカウントを使用して Automanage を有効にするには、VM を含むリソース グループの **共同作成者** ロールが必要です。 新しい Automanage アカウントで Automanage を有効にする場合は、次のアクセス許可が必要です: ご使用のサブスクリプションに対する **所有者** ロール、または **共同作成者** ロールと **ユーザー アクセス管理者** ロールの併用。


## <a name="sign-in-to-azure"></a>Azure へのサインイン

[Azure portal](https://portal.azure.com/) にサインインします。


## <a name="enable-automanage-for-vms-on-an-existing-vm"></a>既存の VM で VM に対して Automanage を有効にする

1. 検索バーで、 **[Automanage – Azure virtual machine best practices]\(Automanage - Azure 仮想マシンのベスト プラクティスの有効化)** を検索して選択します。

2. **[Enable on existing VM]\(既存の VM で有効にする\)** を選択します。

    :::image type="content" source="media\quick-create-virtual-machine-portal\zero-vm-list-view.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)":::

3. **[マシンの選択]** ブレードで次のようにします。
    1. 実際の **サブスクリプション** と **リソース グループ** で VM のリストにフィルターをかけます。
    1. オンボードする各仮想マシンのチェック ボックスをオンにします。
    1. **[選択]** ボタンをクリックします。

    :::image type="content" source="media\quick-create-virtual-machine-portal\existing-vm-select-machine.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)":::

4. **[構成プロファイル]** で、 **[Browse and change profiles and preferences]\(プロファイルと基本設定を参照して変更\)** をクリックします。

    :::image type="content" source="media\quick-create-virtual-machine-portal\existing-vm-quick-create.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)" は運用環境用です。
    1. **[選択]** ボタンをクリックします。

    :::image type="content" source="media\quick-create-virtual-machine-portal\browse-production-profile.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)":::

6. **[有効]** ボタンをクリックします。


## <a name="enable-automanage-for-vms-on-a-new-vm"></a>新規の VM で VM に対して Automanage を有効にする

Azure portal の[こちら](https://aka.ms/automanageportalnextstep)にサインインして、新しい VM を作成し、Automanage を有効にします。

1. [Azure portal で Windows VM を作成するチュートリアル](..\virtual-machines\windows\quick-create-portal.md)の作成手順に従います。

2. VM がデプロイされると、デプロイ ステータスのページが表示され、下部には推奨される **[次の手順]** が表示されます。

    :::image type="content" source="media\quick-create-virtual-machine-portal\create-next-steps.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)":::

3. **[次の手順]** で、 **[Enable Automanage virtual machine best practices]\(仮想マシンの Automanage のベスト プラクティスを有効にする\)** を選択します。

4. **[Automanage – Azure virtual machine best practices]\(Automanage – Azure 仮想マシンのベストプラクティスの有効化\)** ページの **[マシン]** は、新しく作成された VM によって自動的に設定されます。

    :::image type="content" source="media\quick-create-virtual-machine-portal\create-new-enable-overview.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)" は運用環境用です。
    1. **[選択]** ボタンをクリックします。

    :::image type="content" source="media\quick-create-virtual-machine-portal\browse-production-profile.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)":::

7. **[有効]** ボタンをクリックします。

## <a name="disable-automanage-for-vms"></a>VM の Automanage を無効にする

自動管理を無効にすることで、仮想マシンに対する Azure Automanage の使用をすばやく停止します。

:::image type="content" source="media\automanage-virtual-machines\disable-step-1.png" alt-text="[Enable on existing VM]\(既存の VM で有効にする\)":::

1. 自動管理されている VM がすべて表示されている **[Automanage – Azure virtual machine best practices]\(Automanage - Azure 仮想マシンのベスト プラクティス)** ページに移動します。
1. 無効にする仮想マシンの横にあるチェック ボックスをオンにします。
1. **[Disable automanagent]\(自動管理の無効化\)** ボタンをクリックします。
1. 結果として表示されたポップアップのメッセージをよく読んでから、 **[Disable]\(無効\)** に同意します。


## <a name="clean-up-resources"></a>リソースをクリーンアップする

新しいリソース グループを作成して、仮想マシンに対して Azure Automanage を試し、不要になった場合は、そのリソース グループを削除できます。 グループを削除すると、そのリソース グループ内の VM およびすべてのリソースも削除されます。

Azure Automanage では、リソースを格納するための既定のリソース グループが作成されます。 すべてのリソースをクリーンアップするために "DefaultResourceGroupRegionName" および "AzureBackupRGRegionName" という名前付け規則を使用しているリソース グループを確認します。

1. **[リソース グループ]** を選択します。
1. リソース グループのページで、 **[削除]** を選択します。
1. プロンプトが表示されたら、リソース グループ名を確認し、 **[削除]** を選択します。


## <a name="next-steps"></a>次の手順

このクイックスタートでは、VM に対して Azure Automanage を有効にしました。 

仮想マシンで Automanage を有効にする際に、カスタマイズした基本設定を作成して適用する方法を確認してください。 

> [!div class="nextstepaction"]
> [VM の Azure Automanage - カスタム構成プロファイル](virtual-machines-custom-preferences.md)
