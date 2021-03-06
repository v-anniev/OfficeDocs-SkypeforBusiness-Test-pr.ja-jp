﻿---
title: 'Lync Server 2013: 許可された外部ドメイン向けサポートの構成'
TOCTitle: 許可された外部ドメイン向けサポートの構成
ms:assetid: 3ee6e175-986d-4c33-b03a-b9f93083dca6
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg425908(v=OCS.15)
ms:contentKeyID: 48271879
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での、許可された外部ドメイン向けサポートの構成

 

_**トピックの最終更新日:** 2012-10-19_

フェデレーション パートナーに対するサポートが構成されている場合、どのドメインが組織とのフェデレーションを実行できるかに関してユーザーによる管理が可能になります。1 つ以上の特定の外部ドメインを許可されたフェデレーション ドメインとして構成します。この構成を実行するには、各ドメインを許可されたドメインの一覧に追加します。組織についてパートナー検出が有効な場合でも、ドメインが 1,000 を超えるユーザーとの通信が必要になる可能性があるフェデレーション パートナーの場合や、毎秒、20 件を超えるメッセージの送信が必要になる可能性があるフェデレーション パートナーの場合は、この手順を実行してください。組織についてパートナー検出が有効になっていない場合は、許可されたドメインの一覧に追加した外部ドメインに属するユーザーだけが、組織のユーザーとの IM および会議に参加できます。フェデレーション ドメインへのアクセスをフェデレーション パートナーのアクセス エッジ サービスを実行する特定のサーバーに限定する場合は、許可されたドメインの一覧にある各ドメインを対象に、アクセス エッジ サービスを実行するサーバーのドメイン名を指定できます。

> [!NOTE]
> この手順は、特定のドメインに対するサポートの構成方法を記述しますが、フェデレーション ユーザーに対するサポートを実装するには、組織のフェデレーション ユーザーに対するサポートを有効にし、ポリシーを構成および適用して、どのユーザーがフェデレーション ユーザーと共同作業できるかを制御する必要もあります。フェデレーション ユーザーに対するサポートを有効にする方法の詳細については、「<a href="lync-server-2013-enable-or-disable-remote-user-access.md">Lync Server 2013 でのリモート ユーザー アクセスの有効化または無効化</a>」を参照してください。フェデレーションを管理するためのポリシーの構成の詳細については、「<a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Lync Server 2013 でのフェデレーション ユーザー アクセスを制御するポリシーの構成</a>」を参照してください。


## 外部ドメインを許可されたドメインの一覧に追加するには

1.  RTCUniversalServerAdmins グループ (または同等のユーザー権限を持つグループ) のメンバーであるユーザー アカウントまたは CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**外部ユーザー アクセス**\] をクリックし、\[**フェデレーション ドメイン**\] をクリックします。

4.  \[**フェデレーション ドメイン**\] ページで、\[**新規**\] をクリックし、\[**許可されたドメイン**\] をクリックします。

5.  \[**新規フェデレーション ドメイン**\] で、次の操作を実行します。
    
      - \[**ドメイン名 (または FQDN)**\] で、フェデレーション パートナー ドメインの名前を入力します。
        
        > [!NOTE]  
        > この名前は一意である必要があり、アクセス エッジ サービスを実行するこのサーバーの許可されたドメインとして既に存在する名前は指定できません。 名前の長さは、最大 256 文字です。<br />
        > フェデレーション パートナー ドメインの名前についての検索では、サフィックスの一致が実行されます。たとえば、<strong>contoso.com</strong> と入力すると、検索によりドメイン <strong>it.contoso.com</strong> も戻されます。<br />
        > フェデレーション パートナー ドメインを同時に禁止および許可することはできません。Lync Server 2013 がこのような状態の発生を防止するため、ユーザーが一覧の同期を取る必要はありません。
    
      - このフェデレーション ドメインへのアクセスをアクセス エッジ サービスを実行している特定のサーバーのユーザーに限定する場合は、\[**アクセス エッジ サービス (FQDN)**\] で、アクセス エッジ サービスを実行しているフェデレーション ドメインのサーバーの FQDN を入力します。
    
      - 追加情報を提供する場合は、\[**コメント**\] で、この構成について他のシステム管理者と共有する必要のある情報を入力します。

6.  \[**確定**\] をクリックします。

7.  許可するフェデレーション パートナー ドメインごとに、ステップ 4 ～ 6 を繰り返します。

フェデレーション ユーザー アクセスを有効にするには、組織でフェデレーション ユーザー アクセスのサポートも有効にする必要があります。詳細については、「[Lync Server 2013 でのリモート ユーザー アクセスの有効化または無効化](lync-server-2013-enable-or-disable-remote-user-access.md)」を参照してください。

また、ポリシーを構成して、フェデレーション ユーザーと共同作業できるようにするユーザーに適用する必要があります。詳細については、「[Lync Server 2013 でのフェデレーション ユーザー アクセスを制御するポリシーの構成](lync-server-2013-configure-policies-to-control-federated-user-access.md)」を参照してください。

