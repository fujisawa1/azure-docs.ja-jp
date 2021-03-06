---
author: alkohli
ms.service: storsimple
ms.topic: include
ms.date: 10/26/2018
ms.author: alkohli
ms.openlocfilehash: 746198f87e23cd7aca2a3177c23974917cb4b12a
ms.sourcegitcommit: a43a59e44c14d349d597c3d2fd2bc779989c71d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96027233"
---
#### <a name="to-create-a-new-service"></a>新しいサービスを作成するには

1. Microsoft アカウントの資格情報を使用して、[Azure portal](https://portal.azure.com/) にサインインします。

2. Azure Portal で **[リソースの作成]** をクリックし、Marketplace で **[すべて表示]** をクリックします。

    ![StorSimple デバイス マネージャーの作成](./media/storsimple-8000-create-new-service/createssdevman1.png)

    "_StorSimple 物理_" を検索します。 **[StorSimple 物理デバイス シリーズ]** を選択してクリックし、 **[作成]** をクリックします。 または、Azure Portal で **+** をクリックし、 **[ストレージ]** で **[StorSimple 物理デバイス シリーズ]** をクリックします。

    ![StorSimple デバイス マネージャーの作成 2](./media/storsimple-8000-create-new-service/createssdevman11.png)

3. **[StorSimple デバイス マネージャー]** ブレードで、次の操作を実行します。

   1. サービスの一意の **リソース名** を指定します。 この名前は、サービスの識別に使用できる表示名です。 名前の長さは 2 ～ 50 文字とし、文字、数字、ハイフンを含めることができます。 名前の最初と最後は、文字か数字とする必要があります。

   2. **[サブスクリプション]** ボックスの一覧で、サブスクリプションを選択します。 サブスクリプションは、課金アカウントにリンクされます。 このフィールドは、保有するサブスクリプションが 1 つだけの場合は表示されません。

   3. **リソース グループ** は、**既存のグループを使用** するか、**新しいグループを作成** します。 詳細については、[Azure のリソース グループ](../articles/azure-resource-manager/management/manage-resource-groups-portal.md)に関する記事をご覧ください。

   4. サービスの **[場所]** を指定します。 一般的に、デバイスをデプロイする地理的リージョンに最も近い場所を選択します。 次の点についても考慮してください。

      * Azure 内の既存のワークロードを StorSimple デバイスにもデプロイする場合、そのデータセンターを使用する必要があります。
      * StorSimple デバイス マネージャー サービスと Azure Storage は別々の場所に置くことができます。 その場合、StorSimple デバイス マネージャーと Azure ストレージ アカウントを別々に作成する必要があります。 Azure ストレージ アカウントを作成するには、Azure Portal で Azure Storage サービスに移動し、「[ストレージ アカウントの作成](../articles/storage/common/storage-account-create.md)」に記載されている手順に従います。 このアカウントを作成したら、「[サービスの新しいストレージ アカウントを構成する](../articles/storsimple/storsimple-8000-deployment-walkthrough-u2.md#configure-a-new-storage-account-for-the-service)」に記載されている手順に従って、StorSimple デバイス マネージャー サービスにアカウントを追加します。

   5. **[新しいストレージ アカウントを作成する]** をオンにすると、サービスの作成時にストレージ アカウントが自動的に作成されます。 このストレージ アカウントの名前を指定します。 別の場所でデータが必要になる場合、このボックスをオフにします。

   6. ダッシュボードにこのサービスへのクイック リンクが必要な場合、 **[ダッシュボードにピン留めする]** チェック ボックスをオンにします。

   7. **[作成]** をクリックして、StorSimple デバイス マネージャーを作成します。

       ![StorSimple デバイス マネージャーの作成 3](./media/storsimple-8000-create-new-service/createssdevman2.png)

サービスの作成には数分かかります。 サービスが正常に作成されると、通知が表示され、新しいサービス ブレードが開きます。

![StorSimple デバイス マネージャーの作成 4](./media/storsimple-8000-create-new-service/createssdevman5.png)