﻿---
title: 'Lync Server 2013: 存続可能ブランチ アプライアンスまたは存続可能ブランチ サーバーの定義'
TOCTitle: 存続可能ブランチ アプライアンスまたは存続可能ブランチ サーバーの定義
ms:assetid: 1f49cfbe-30b3-4600-af15-47cb2f58d18a
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398280(v=OCS.15)
ms:contentKeyID: 48271468
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での存続可能ブランチ アプライアンスまたは存続可能ブランチ サーバーの定義

 

_**トピックの最終更新日:** 2012-10-07_

存続可能ブランチ アプライアンスまたは存続可能ブランチ サーバーをトポロジに追加した際にこれを定義しなかった場合は、この手順をセントラル サイトで実行します。

## 存続可能ブランチ アプライアンスまたは 存続可能ブランチ サーバーを定義するには

1.  \[**スタート**\]、\[**すべてのプログラム**\]、\[**Microsoft Lync Server 2013**\]、\[**Lync Serverトポロジ ビルダー**\] の順にクリックします。

2.  コンソール ツリーでセントラル サイトを展開し、\[**ブランチ サイト**\] を展開してから、存続可能ブランチ アプライアンスまたは 存続可能ブランチ サーバーを展開する予定のブランチ サイトの名前を展開します。

3.  \[**存続可能ブランチ アプライアンス**\] を右クリックし、\[**新しい 存続可能ブランチ アプライアンス**\] をクリックします。
    

    > [!IMPORTANT]
    > 存続可能ブランチ サーバーおよび 存続可能ブランチ アプライアンスの定義は [<STRONG>存続可能ブランチ アプライアンス</STRONG>] で行います。



4.  \[**存続可能ブランチ アプライアンスの定義** \] ダイアログ ボックスで、\[**FQDN**\] をクリックし、このブランチ サイトで展開予定の存続可能ブランチ アプライアンスまたは存続可能ブランチ サーバーの完全修飾ドメイン名 (FQDN) を入力して、\[**次へ**\] をクリックします。
    

    > [!IMPORTANT]
    > 存続可能ブランチ アプライアンスを定義する場合、[<STRONG>FQDN</STRONG>] に入力する名前は、<STRONG>servicePrincipalName</STRONG> 属性に割り当てた 存続可能ブランチ アプライアンスの FQDN と同じである必要があります。詳細については、「<A href="lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md">Lync Server 2013 での、Active Directory への存続可能ブランチ アプライアンスの追加</A>」を参照してください。



5.  \[**フロントエンド プール**\] をクリックし、この 存続可能ブランチ アプライアンスまたは 存続可能ブランチ サーバーの接続先となるセントラル サイトでフロントエンド サーバー (ユーザー サービス プール) をクリックし、\[**次へ**\] をクリックします。

6.  \[**エッジ サーバー**\] をクリックし、この 存続可能ブランチ アプライアンスまたは 存続可能ブランチ サーバーの接続先となるエッジ プールをクリックしてブランチ サイトのリモート ユーザーと PSTN 接続してから \[**次へ**\] をクリックします。

7.  \[**ゲートウェイの FQDN または IP アドレス**\] をクリックし、存続可能ブランチ アプライアンスまたは 存続可能ブランチ サーバーが関連付けられているゲートウェイ ピアの FQDN または IP アドレスを入力して、PSTN 通話の着信や発信をルーティングします。
    

    > [!IMPORTANT]
    > 存続可能ブランチ アプライアンスを定義している場合、これは PSTN 接続で 存続可能ブランチ アプライアンス内部の仲介サーバーが接続するゲートウェイとなります。



8.  \[**IP/PSTN ゲートウェイのリッスン ポート**\] をクリックし、既定のポートに設定します。

9.  \[**SIP トランスポート プロトコル**\] で、存続可能ブランチ アプライアンスや 存続可能ブランチ サーバーが使用するトランスポート プロトコルをクリックし、\[**完了**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>セキュリティ上の理由により、トランスポート層セキュリティ (TLS) を使用することを強くお勧めします。 存続可能ブランチ アプライアンスを定義する場合は、存続可能ブランチ アプライアンスのベンダー ドキュメントを参照して、ご使用の 存続可能ブランチ アプライアンスが TLS プロトコルをサポートしていることを確認してください。</td>
    </tr>
    </tbody>
    </table>


10. コンソール ツリーで新しい存続可能ブランチ アプライアンスまたは存続可能ブランチ サーバーを右クリックし、\[**トポロジ**\] をクリックしてから \[**公開**\] をクリックします。

**次のステップ**: [Lync Server 2013 での存続可能ブランチ アプライアンスまたは存続可能ブランチ サーバーの展開 - ブランチ サイトのタスク](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)
