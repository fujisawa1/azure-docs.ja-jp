---
author: alkohli
ms.service: storsimple
ms.topic: include
ms.date: 10/26/2018
ms.author: alkohli
ms.openlocfilehash: e3bff61cfbf89aee3566d677ccf593b102cff36d
ms.sourcegitcommit: 6a902230296a78da21fbc68c365698709c579093
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "93376036"
---
#### <a name="to-add-a-storsimple-backup-policy"></a>StorSimple のバックアップ ポリシーを追加するには

1. StorSimple デバイスに移動して、 **[バックアップ ポリシー]** をクリックします。

2. **[バックアップ ポリシー]** ブレードのコマンド バーで、 **[ポリシーの追加]** をクリックします。
   
    ![バックアップ ポリシーを追加する](./media/storsimple-8000-add-backup-policy-u2/addbupol1.png)

3. **[バックアップ ポリシーの作成]** ブレードで、次の操作を行います。
   
   1. **[デバイスの選択]** は、選択したデバイスに基づいて自動的に設定されます。
   
   2. バックアップ **ポリシー名** として 3 ～ 150 文字の名前を指定します。 ポリシーを作成した後にポリシーの名前を変更することはできません。
       
   3. このバックアップ ポリシーにボリュームを割り当てるには、 **[ボリュームの追加]** を選択してから、ボリュームの表形式の一覧でチェック ボックスをオンにして、1 つまたは複数のボリュームをこのバックアップ ポリシーに割り当てます。

       ![バックアップ ポリシー 2 の追加](./media/storsimple-8000-add-backup-policy-u2/addbupol2.png)

   4. このバックアップ ポリシーのスケジュールを定義するには、 **[最初のスケジュール]** をクリックしてから、次のパラメーターを変更します。

       ![バックアップ ポリシーの追加 3](./media/storsimple-8000-add-backup-policy-u2/addbupol3.png)

       1. **[スナップショットの種類]** で、 **[クラウド]** または **[ローカル]** を選択します。

       2. バックアップの頻度を指定します (数値を指定し、ドロップダウン リストから **[日]** または **[週間]** を選択します)。

       3. 保持スケジュールを入力します。

       4. バックアップ ポリシーの開始日時を入力します。

       5. **[OK]** をクリックして、スケジュールを定義します。

   5. **[作成]** をクリックして、バックアップ ポリシーを作成します。

       ![バックアップ ポリシーの追加 4](./media/storsimple-8000-add-backup-policy-u2/addbupol4.png)
   
   6. バックアップ ポリシーが作成されると、その旨が通知されます。 **[バックアップ ポリシー]** ブレードの表形式のビューに、新たに追加したポリシーが表示されます。

       ![バックアップ ポリシーの追加 5](./media/storsimple-8000-add-backup-policy-u2/addbupol7.png)

