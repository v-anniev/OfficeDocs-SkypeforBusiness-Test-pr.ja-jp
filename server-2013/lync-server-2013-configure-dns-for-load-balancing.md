﻿---
title: 'Lync Server 2013: 負荷分散の DNS 構成'
TOCTitle: 負荷分散の DNS 構成
ms:assetid: 1b2e8414-8676-4872-8ecf-ea07196f74de
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398251(v=OCS.15)
ms:contentKeyID: 48271408
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での負荷分散の DNS 構成

 

_**トピックの最終更新日:** 2015-03-09_

この手順を正常に完了するには、最低限でも Domain Admins グループまたは DnsAdmins グループのメンバーとしてサーバーまたはドメインにログオンしている必要があります。

ドメイン ネーム システム (DNS) 負荷分散では、SIP トラフィックやメディア トラフィックなど、Lync Server 2013 に固有のネットワーク トラフィックを分散します。DNS 負荷分散は、フロントエンド プール、エッジ プール、ディレクター プール、およびスタンドアロンの仲介プールでサポートされています。DNS 負荷分散を使用するように構成されているプールでは、2 つの完全修飾ドメイン名 (FQDN) が定義されている必要があります。1 つは DNS 負荷分散が使用する標準プールの FQDN (pool1.contoso.com など) で、プール内のサーバーの物理 IP に解決されます。もう 1 つは、プールの Web サービスの FQDN (web1.contoso.net など) で、プールの仮想 IP アドレスに解決されます。DNS 負荷分散の詳細については、「計画」のドキュメントの「[Lync Server 2013 での DNS 負荷分散](lync-server-2013-dns-load-balancing.md)」を参照してください。

> [!NOTE]
> クライアントからサーバーへの HTTPS トラフィックには、まだハードウェア負荷分散が必要です。


DNS 負荷分散を使用する前に、次の操作を行う必要があります。

1.  内部の Web サービス プールの FQDN のオーバーライド
    

    > [!WARNING]
    > 独自に定義した FQDN で内部 Web サービスを上書きする場合は、各 FQDN は他の フロント エンド プール、ディレクター、または ディレクター プールとは別のものにする必要があります。



2.  プールの FQDN をプール内のすべてのサーバーの IP アドレスに解決するための DNS A ホスト レコードの作成

3.  IP アドレスのランダム化を有効にする (Windows Server の DNS の場合は、ラウンド ロビンを有効にする)
    
    > [!NOTE]
    > ラウンド ロビンは既定で有効になっています。


## 内部 Web サービスの FQDN をオーバーライドするには

1.  トポロジ ビルダーを以下の手順で起動します。\[**スタート**\]、\[**すべてのプログラム**\]、\[**Microsoft Lync Server 2013**\]、\[**Lync Server トポロジ ビルダー**\] の順にクリックします。

2.  コンソール ツリーから、Enterprise Edition のフロントエンド プールのノードを展開します。

3.  プールを右クリックして \[**プロパティの編集**\] をクリックし、\[**Web サービス**\] をクリックします。

4.  \[**内部 Web サービス**\] で、\[**FQDN のオーバーライド**\] チェック ボックスをオンにします。

5.  プール内のサーバーの物理 IP アドレスへ解決するプールの FQDN を入力します。

6.  \[**外部 Web サービス**\] で、プールの仮想 IP アドレスへ解決する外部プールの FQDN を入力し、\[**OK**\] をクリックします。

7.  コンソール ツリーから \[**Lync Server 2013**\] をクリックし、次に \[**操作**\] ウィンドウで \[**トポロジの公開**\] をクリックします。

## すべての内部プール サーバーの DNS ホスト (A) レコードを作成するには

1.  \[**スタート**\] をクリックし、\[**すべてのプログラム**\]、\[**管理ツール**\] をクリックし、\[**DNS**\] をクリックします。

2.  \[**DNS マネージャー**\] で、レコードを管理する DNS サーバーをクリックして展開します。

3.  \[**前方参照ゾーン**\] をクリックして展開します。

4.  レコードの追加が必要な DNS ドメインを右クリックし、\[**新しいホスト (A または AAAA)**\] をクリックします。

5.  \[**名前**\] ボックスにホスト レコード名を入力します (ドメイン名は自動的に追加されます)。

6.  \[IP アドレス\] ボックスで、個々のフロントエンド サーバーの IP アドレスを入力し、適用可能な場合は \[**関連付けられたポインター (PTR) レコードを作成する**\] または \[**同じ所有者名の DNS レコードの更新を認証されたユーザーに許可する**\] を選択します。

7.  引き続き、DNS 負荷分散に参加するすべてのメンバー フロントエンド サーバーのレコードを作成します。
    
    たとえば、pool1.contoso.com という名前のプールと 3 台のフロントエンド サーバーがある場合は、次の DNS エントリを作成します。
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>FQDN</th>
    <th>型</th>
    <th>データ</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>ホスト (A)</p></td>
    <td><p>192.168.1.1</p></td>
    </tr>
    <tr class="even">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>ホスト (A)</p></td>
    <td><p>192.168.1.2</p></td>
    </tr>
    <tr class="odd">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>ホスト (A)</p></td>
    <td><p>192.168.1.3</p></td>
    </tr>
    </tbody>
    </table>
    
    DNS ホスト (A) レコードの作成の詳細については、「[Lync Server 2013 での DNS ホスト レコードの構成](lync-server-2013-configure-dns-host-records.md)」を参照してください。

## Windows Server のラウンド ロビンを有効にするには

1.  \[**スタート**\] をクリックし、\[**すべてのプログラム**\]、\[**管理ツール**\] をクリックし、\[**DNS**\] をクリックします。

2.  \[**DNS**\] を展開し、構成する DNS サーバーを右クリックして、\[**プロパティ**\] をクリックします。

3.  \[**詳細設定**\] タブをクリックし、\[**ラウンド ロビンを有効にする**\] と \[**ネットマスクの順序を有効にする**\] を選択して、\[**OK**\] をクリックします。
    
    ![DNS ラウンド ロビン ダイアログ ボックス](images/Gg398251.e7bf6125-8d78-4460-8401-0a8e7e21d305(OCS.15).jpg "DNS ラウンド ロビン ダイアログ ボックス")

> [!NOTE]
> この機能は既定で有効になっています。


## 関連項目

#### 概念

[Lync Server 2013 での DNS 負荷分散](lync-server-2013-dns-load-balancing.md)

