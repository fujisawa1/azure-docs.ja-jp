---
title: Azure NetApp Files のリージョン間レプリケーションのトラブルシューティング | Microsoft Docs
description: Azure NetApp Files のリージョン間レプリケーションに関する問題のトラブルシューティングに役立つエラー メッセージと解決策について説明します。
services: azure-netapp-files
documentationcenter: ''
author: b-juche
manager: ''
editor: ''
ms.assetid: ''
ms.service: azure-netapp-files
ms.workload: storage
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: troubleshooting
ms.date: 11/18/2020
ms.author: b-juche
ms.openlocfilehash: b30ed0cca680013b85efe064d59fb7cb73d753d2
ms.sourcegitcommit: 30906a33111621bc7b9b245a9a2ab2e33310f33f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2020
ms.locfileid: "95239552"
---
# <a name="troubleshoot-cross-region-replication"></a>リージョン間レプリケーションのトラブルシューティング

この記事では、Azure NetApp Files のリージョン間レプリケーションに関する問題のトラブルシューティングに役立つエラー メッセージと解決策について説明します。 

## <a name="errors-creating-replication"></a>レプリケーションの作成中に発生するエラー  

|     エラー メッセージ    |     解決策    |
|-|-|
|     `Volume {0} cannot   be used as source because it is already in replication`    |     既にデータ レプリケーション関係にあるソース ボリュームを使用してレプリケーションを作成することはできません。    |
|     `Peered region   '{0}' is not accepted`    |     ピアリングされていないリージョン間のレプリケーションを作成しようとしています。    |
|     `RemoteVolumeResource   '{0}' of wrong type '{1}'`    |     リモート リソース ID がボリューム リソース ID であることを確認します。    |

## <a name="errors-authorizing-volume"></a>ボリュームの承認中に発生するエラー  

|     エラー メッセージ    |     解決策    |
|-|-|
|     `Missing value   for 'AuthorizeSourceReplication'`    |     UI または API 要求から取得された `RemoteResourceID` が見つからないか無効です (エラー メッセージを解決してください)。    |
|     `Missing value   for 'RemoteVolumeResourceId'`    |     UI または API の要求から取得された `RemoteResourceID` が見つからないか無効です。    |
|     `Data   Protection volume not found for RemoteVolumeResourceId: {remoteResourceId}`    |     ユーザーの `RemoteResourceID` が正しいかどうか、または存在するかどうかを確認します。    |
|     `Remote volume   '{0}' is not configured for replication`    |     ターゲット ボリュームがデータ保護ボリュームではありません。    |
|     `Remote volume   '{0}' does not have source volume '{1}' as RemoteVolumeResourceId`    |     データ保護ボリュームのリモート リソース ID にこのソース ボリュームがありません (間違ったソース ID が入力されました)。    |
|     `The   destination volume replication creation failed (message: {0})`    |     このエラーはサーバー エラーを示しています。 サポートにお問い合わせください。    |

## <a name="errors-deleting-replication"></a>レプリケーションの削除中に発生するエラー

|     エラー メッセージ    |     解決策    |
|-|-|
|     `Replication   cannot be deleted, mirror state needs to be in status: Broken before deleting`    |     レプリケーションが解除されているか、または初期化されずにアイドル状態になっている (初期化に失敗した) かを確認します。    |
|     `Cannot delete   source replication`    |     ソース側からのレプリケーションの削除は許可されていません。 ターゲット側からレプリケーションを削除していることを確認します。    |

## <a name="errors-deleting-volume"></a>ボリュームの削除中に発生するエラー

|     エラー メッセージ    |     解決策    |
|-|-|
| `Volume is a member of an active volume replication relationship`  |  ボリュームを削除する前に、レプリケーションを削除します。 「[レプリケーションの削除](cross-region-replication-delete.md)」を参照してください。 この操作では、ボリュームのレプリケーションを削除する前にピアリングを中断する必要があります。 |
| `Volume with replication cannot be deleted`  |  ボリュームを削除する前に、レプリケーションを削除します。 「[レプリケーションの削除](cross-region-replication-delete.md)」を参照してください。 この操作では、ボリュームのレプリケーションを削除する前にピアリングを中断する必要があります。 

## <a name="errors-resyncing-volume"></a>ボリュームの再同期中に発生するエラー

|     エラー メッセージ    |     解決策    |
|-|-|
|     `Volume Replication is in invalid status: (Mirrored|Uninitialized) for operation: 'ResyncReplication'`     |     ボリュームのレプリケーションが "解除済み" 状態であることを確認します。    |

## <a name="errors-deleting-snapshot"></a>スナップショットの削除中に発生するエラー 

|     エラー メッセージ    |     解決策    |
|-|-|
|     `Snapshot   cannot be deleted, parent volume is a Data Protection volume with a   replication object`    |     このスナップショットを削除する場合は、ボリュームのレプリケーションが解除済みであることを確認します。    |
|     `Cannot delete   volume replication generated snapshot`    |     レプリケーションのベースライン スナップショットの削除は許可されていません。    |

## <a name="next-steps"></a>次のステップ  

* [リージョン間レプリケーション](cross-region-replication-introduction.md)
* [リージョン間レプリケーションを使用するための要件と考慮事項](cross-region-replication-requirements-considerations.md)
* [ボリューム レプリケーションを作成する](cross-region-replication-create-peering.md)
* [レプリケーション関係の正常性状態を表示する](cross-region-replication-display-health-status.md)
* [ディザスター リカバリーの管理](cross-region-replication-manage-disaster-recovery.md)
* [リージョン間レプリケーションのトラブルシューティング](troubleshoot-cross-region-replication.md)
