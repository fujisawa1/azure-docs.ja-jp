---
title: チュートリアル:ServiceNow を構成し、Azure Active Directory を使用した自動ユーザー プロビジョニングに対応させる | Microsoft Docs
description: Azure AD から ServiceNow に対してユーザー アカウントを自動的にプロビジョニング/プロビジョニング解除する方法を説明します。
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: celested
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 12/10/2019
ms.author: jeedes
ms.openlocfilehash: 928b8118c614d7d16293c8d6e0cec194a270314e
ms.sourcegitcommit: 78ecfbc831405e8d0f932c9aafcdf59589f81978
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2021
ms.locfileid: "98729925"
---
# <a name="tutorial-configure-servicenow-for-automatic-user-provisioning"></a>チュートリアル:自動ユーザー プロビジョニングのために ServiceNow を構成する

このチュートリアルでは、自動ユーザー プロビジョニングを構成するために ServiceNow と Azure Active Directory (Azure AD) の両方で実行する必要がある手順について説明します。 構成すると、Azure AD では、ユーザーとグループの [ServiceNow](https://www.servicenow.com/) へのプロビジョニングおよびプロビジョニング解除が Azure AD プロビジョニング サービスを使って自動的に行われるようになります。 このサービスが実行する内容、しくみ、よく寄せられる質問の重要な詳細については、「[Azure Active Directory による SaaS アプリへのユーザー プロビジョニングとプロビジョニング解除の自動化](../app-provisioning/user-provisioning.md)」を参照してください。 


## <a name="capabilities-supported"></a>サポートされる機能
> [!div class="checklist"]
> * ServiceNow でユーザーを作成する
> * アクセスが不要になった場合に ServiceNow のユーザーを削除する
> * Azure AD と ServiceNow の間でユーザー属性の同期を維持する
> * ServiceNow でグループとグループ メンバーシップをプロビジョニングする
> * ServiceNow への[シングル サインオン](servicenow-tutorial.md) (推奨)

## <a name="prerequisites"></a>前提条件

このチュートリアルで説明するシナリオでは、次の前提条件目があることを前提としています。

* [Azure AD テナント](../develop/quickstart-create-new-tenant.md) 
* プロビジョニングを構成するための[アクセス許可](../roles/permissions-reference.md)を持つ Azure AD のユーザー アカウント (アプリケーション管理者、クラウド アプリケーション管理者、アプリケーション所有者、グローバル管理者など)。 
* Calgary 以降の [ServiceNow インスタンス](https://www.servicenow.com/)
* Helsinki 以降の [ServiceNow Express インスタンス](https://www.servicenow.com/)
* 管理者ロールを持つ ServiceNow のユーザー アカウント

## <a name="step-1-plan-your-provisioning-deployment"></a>手順 1. プロビジョニングのデプロイを計画する
1. [プロビジョニング サービスのしくみ](../app-provisioning/user-provisioning.md)を確認します。
2. [プロビジョニングの対象](../app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md)となるユーザーを決定します。
3. [Azure AD と ServiceNow の間でマップする](../app-provisioning/customize-application-attributes.md)データを決定します。 

## <a name="step-2-configure-servicenow-to-support-provisioning-with-azure-ad"></a>手順 2. Azure AD でのプロビジョニングをサポートするように ServiceNow を構成する

1. ServiceNow インスタンス名を指定します。 インスタンス名は、ServiceNow にアクセスするために使用する URL で確認できます。 次の例では、インスタンス名は dev35214 です。

   ![ServiceNow インスタンス](media/servicenow-provisioning-tutorial/servicenow-instance.png)

2. ServiceNow で管理者の資格情報を取得します。 ServiceNow のユーザー プロファイルに移動し、ユーザーが管理者ロールを持っていることを確認します。 

   ![ServiceNow 管理者ロール](media/servicenow-provisioning-tutorial/servicenow-admin-role.png)


## <a name="step-3-add-servicenow-from-the-azure-ad-application-gallery"></a>手順 3. Azure AD アプリケーション ギャラリーから ServiceNow を追加する

Azure AD アプリケーション ギャラリーから ServiceNow を追加して、ServiceNow へのプロビジョニングの管理を開始します。 SSO のために ServiceNow を以前に設定した場合は、その同じアプリケーションを使用できます。 ただし、統合を初めてテストするときは、別のアプリを作成することをお勧めします。 ギャラリーからアプリケーションを追加する方法の詳細については、[こちら](../manage-apps/add-application-portal.md)を参照してください。 

## <a name="step-4-define-who-will-be-in-scope-for-provisioning"></a>手順 4. プロビジョニングの対象となるユーザーを定義する 

Azure AD プロビジョニング サービスを使用すると、アプリケーションへの割り当て、ユーザーまたはグループの属性に基づいてプロビジョニングされるユーザーのスコープを設定できます。 割り当てに基づいてアプリにプロビジョニングされるユーザーのスコープを設定する場合、以下の[手順](../manage-apps/assign-user-or-group-access-portal.md)を使用して、ユーザーとグループをアプリケーションに割り当てることができます。 ユーザーまたはグループの属性のみに基づいてプロビジョニングされるユーザーのスコープを設定する場合、[こちら](../app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md)で説明されているスコープ フィルターを使用できます。 

* ServiceNow にユーザーとグループを割り当てるときは、**既定のアクセス** 以外のロールを選択する必要があります。 既定のアクセス ロールを持つユーザーは、プロビジョニングから除外され、プロビジョニング ログで実質的に資格がないとマークされます。 アプリケーションで使用できる唯一のロールが既定のアクセス ロールである場合は、[アプリケーション マニフェストを更新](../develop/howto-add-app-roles-in-azure-ad-apps.md)してロールを追加することができます。 

* 小さいところから始めましょう。 全員にロールアウトする前に、少数のユーザーとグループでテストします。 プロビジョニングのスコープが割り当て済みユーザーとグループに設定される場合、これを制御するには、1 つまたは 2 つのユーザーまたはグループをアプリに割り当てます。 スコープがすべてのユーザーとグループに設定されている場合は、[属性ベースのスコープ フィルター](../app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md)を指定できます。 


## <a name="step-5-configure-automatic-user-provisioning-to-servicenow"></a>手順 5. ServiceNow への自動ユーザー プロビジョニングを構成する 

このセクションでは、Azure AD でのユーザー、グループ、またはその両方の割り当てに基づいて、TestApp でユーザー、グループ、またはその両方が作成、更新、および無効化されるように Azure AD プロビジョニング サービスを構成する手順について説明します。

### <a name="to-configure-automatic-user-provisioning-for-servicenow-in-azure-ad"></a>Azure AD で ServiceNow の自動ユーザー プロビジョニングを構成するには:

1. [Azure portal](https://portal.azure.com) にサインインします。 **[エンタープライズ アプリケーション]** を選択し、 **[すべてのアプリケーション]** を選択します。

    ![[エンタープライズ アプリケーション] ブレード](common/enterprise-applications.png)

2. アプリケーションの一覧で **[ServiceNow]** を選択します。

    ![アプリケーションの一覧の ServiceNow リンク](common/all-applications.png)

3. **[プロビジョニング]** タブを選択します。

    ![[プロビジョニング] オプションが強調表示された [管理] オプションのスクリーンショット。](common/provisioning.png)

4. **[プロビジョニング モード]** を **[自動]** に設定します。

    ![[自動] オプションが強調表示された [プロビジョニング モード] ドロップダウン リストのスクリーンショット。](common/provisioning-automatic.png)

5. **[管理者資格情報]** セクションで、ServiceNow 管理者の資格情報とユーザー名を入力します。 **[接続テスト]** をクリックして、Azure AD から ServiceNow に確実に接続できるようにします。 接続できない場合は、使用中の ServiceNow アカウントで管理者アクセス許可を確保してから、もう一度試します。

    ![スクリーンショットには、管理者資格情報を入力できる [サービス プロビジョニング] ページが示されています。](./media/servicenow-provisioning-tutorial/servicenow-provisioning.png)

6. **[通知用メール]** フィールドに、プロビジョニングのエラー通知を受け取るユーザーまたはグループの電子メール アドレスを入力して、 **[エラーが発生したときにメール通知を送信します]** チェック ボックスをオンにします。

    ![通知用メール](common/provisioning-notification-email.png)

7. **[保存]** を選択します。

8. **[マッピング]** セクションの **[Azure Active Directory ユーザーを ServiceNow に同期する]** を選択します。

9. **[属性マッピング]** セクションで、Azure AD から ServiceNow に同期されるユーザー属性を確認します。 **[照合]** プロパティとして選択されている属性は、更新処理で ServiceNow のユーザー アカウントとの照合に使用されます。 [一致する対象の属性](../app-provisioning/customize-application-attributes.md)を変更する場合は、その属性に基づいたユーザーのフィルター処理が確実に ServiceNow API でサポートされているようにする必要があります。 **[保存]** ボタンをクリックして変更をコミットします。

10. **[マッピング]** セクションの **[Synchronize Azure Active Directory Groups to ServiceNow]\(Azure Active Directory グループを ServiceNow に同期する\)** を選択します。

11. **[属性マッピング]** セクションで、Azure AD から ServiceNow に同期されるグループ属性を確認します。 **[Matching]\(照合\)** プロパティとして選択されている属性は、更新処理で ServiceNow のグループとの照合に使用されます。 **[保存]** ボタンをクリックして変更をコミットします。

12. スコープ フィルターを構成するには、[スコープ フィルターのチュートリアル](../app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md)の次の手順を参照してください。

13. ServiceNow に対して Azure AD プロビジョニング サービスを有効にするには、 **[設定]** セクションで **[プロビジョニングの状態]** を **[オン]** に変更します。

    ![プロビジョニングの状態を [オン] に切り替える](common/provisioning-toggle-on.png)

14. **[設定]** セクションの **[スコープ]** で目的の値を選択して、ServiceNow にプロビジョニングするユーザーやグループを定義します。

    ![プロビジョニングのスコープ](common/provisioning-scope.png)

15. プロビジョニングの準備ができたら、 **[保存]** をクリックします。

    ![プロビジョニング構成の保存](common/provisioning-configuration-save.png)

この操作により、 **[設定]** セクションの **[スコープ]** で定義したすべてのユーザーとグループの初期同期サイクルが開始されます。 初期サイクルは後続の同期よりも実行に時間がかかります。後続のサイクルは、Azure AD のプロビジョニング サービスが実行されている限り約 40 分ごとに実行されます。 

## <a name="step-6-monitor-your-deployment"></a>手順 6. デプロイを監視する
プロビジョニングを構成したら、次のリソースを使用してデプロイを監視します。

1. [プロビジョニング ログ](../reports-monitoring/concept-provisioning-logs.md)を使用して、正常にプロビジョニングされたユーザーと失敗したユーザーを特定します。
2. [進行状況バー](../app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user.md)を確認して、プロビジョニング サイクルの状態と完了までの時間を確認します。
3. プロビジョニング構成が異常な状態になったと考えられる場合、アプリケーションは検疫されます。 検疫状態の詳細については、[こちら](../app-provisioning/application-provisioning-quarantine-status.md)を参照してください。  

## <a name="troubleshooting-tips"></a>トラブルシューティングのヒント
* **InvalidLookupReference:** ServiceNow の Department や Location などの特定の属性をプロビジョニングする場合、値は ServiceNow の参照テーブルに既に存在している必要があります。 たとえば、ServiceNow の **テーブル名の挿入** テーブルに 2 つの場所 (シアトル、ロサンゼルス) と 3 つの部門 (営業、財務、マーケティング) があるとします。 部門が "営業" で場所が "シアトル" のユーザーをプロビジョニングしようとすると、ユーザーは正常にプロビジョニングされます。 部門 "営業" と場所 "LA" のユーザーをプロビジョニングしようとすると、ユーザーはプロビジョニングされません。 LA という場所を ServiceNow の参照テーブルに追加するか、ServiceNow の形式に合わせて Azure AD のユーザー属性を更新する必要があります。 
* **EntryJoiningPropertyValueIsMissing:** [属性マッピング](../app-provisioning/customize-application-attributes.md)を確認して、一致する属性を特定します。 この値は、プロビジョニング対象のユーザーまたはグループに存在する必要があります。 
* [ServiceNow SOAP API](https://docs.servicenow.com/bundle/newyork-application-development/page/integrate/web-services-apis/reference/r_DirectWebServiceAPIFunctions.html) を確認して、要件や制限事項 (たとえば、ユーザーの国番号を指定するための形式) を理解してください。
* プロビジョニング要求は、既定では https://{your-instance-name}.service-now.com/{table-name} に送信されます。 カスタム テナント URL が必要な場合は、[インスタンス名] フィールドに URL 全体を指定できます。
* **ServiceNowInstanceInvalid** 
  
  `Details: Your ServiceNow instance name appears to be invalid.  Please provide a current ServiceNow administrative user name and          password along with the name of a valid ServiceNow instance.`                                                              

   このエラーは、ServiceNow インスタンスとの通信の問題を示しています。 
   
   テスト接続の問題が発生した場合は、ServiceNow で次の設定を **無効** としてみてください。
   
   1. **[System Security] (システム セキュリティ)**  >  **[High security settings] (高セキュリティ設定)**  >  **[Require basic authentication for incoming SCHEMA requests] (受信 SCHEMA 要求で基本認証を要求する)** と選択します。
   2. **[System Properties] (システム プロパティ)**  >  **[Web サービス]**  >  **[Require basic authorization for incoming SOAP requests] (受信 SOAP 要求で基本認証を要求する)** と選択します。

   ![SOAP 要求の承認](media/servicenow-provisioning-tutorial/servicenow-webservice.png)

   これで問題が解決した場合は、ServiceNow サポートに連絡し、トラブルシューティングに役立てるために SOAP デバッグを有効にするように依頼してください。 

* **IP 範囲** 

   現在、Azure AD のプロビジョニング サービスは特定の IP 範囲下で動作します。そのため、必要であれば他の IP 範囲を制限し、それらの特定の IP 範囲をアプリケーションの許可リストに追加して、Azure AD プロビジョニング サービスからアプリケーションへのトラフィック フローを許可することができます。「[IP 範囲](../app-provisioning/use-scim-to-provision-users-and-groups.md#ip-ranges)」を参照してください。

## <a name="additional-resources"></a>その他のリソース

* [エンタープライズ アプリのユーザー アカウント プロビジョニングの管理](../app-provisioning/configure-automatic-user-provisioning-portal.md)
* [Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](../manage-apps/what-is-single-sign-on.md)

## <a name="next-steps"></a>次のステップ

* [プロビジョニング アクティビティのログの確認方法およびレポートの取得方法](../app-provisioning/check-status-user-account-provisioning.md)