﻿---
title: 'Lync Server 2013: DNS インフラストラクチャのサポート'
TOCTitle: ドメイン ネーム システム (DNS) インフラストラクチャのサポート
ms:assetid: 37777c16-94ce-436d-b517-bcf53a564513
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg425850(v=OCS.15)
ms:contentKeyID: 48271767
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での DNS インフラストラクチャのサポート

 

_**トピックの最終更新日:** 2013-03-08_

Lync Server 2013 では、ドメイン ネーム システム (DNS) が必要であり、次の方法で使用されます。

  - サーバー間通信用の内部のサーバーまたはプールを検出する。

  - クライアントによる、さまざまな SIP トランザクションに使用されるフロントエンド プールまたは Standard Edition サーバーの検出を有効にする。

  - 会議用の簡易 URL をこれらの会議をホストするサーバーに関連付ける。

  - 外部のサーバーおよびクライアントによる、インスタント メッセージング (IM) または会議用のエッジ サーバーまたは HTTP リバース プロキシへの接続を有効にする。

  - ログインされていない統合コミュニケーション (UC) デバイスによる、デバイス更新 Web サービスを実行しているフロントエンド プールまたは Standard Edition サーバーの検出、更新プログラムの取得、およびログの送信を有効にする。

  - モバイル クライアントによる、ユーザーがデバイスの設定で URL を手動で入力する必要がない、Web サービス リソースの自動検出を有効にする。

  - DNS 負荷分散のため。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 2013 は、国際化ドメイン名 (IDN) をサポートしません。</td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> 指定する名前が、サーバーで構成されているコンピューター名と同じである必要があります。既定では、ドメインに参加していないコンピューターのコンピューター名は、完全修飾ドメイン名 (FQDN) ではなく短い名前です。トポロジ ビルダーでは、短い名前ではなく FQDN を使用します。そのため、エッジ サーバーとして展開する、ドメインに参加していないコンピューターの名前で DNS サフィックスを構成する必要があります。Lync Server、エッジ サーバー、およびプールの FQDN を割り当てる場合に使用できる文字は、<STRONG>標準文字のみ</STRONG> (A ～ Z、a ～ z、0 ～ 9、およびハイフン) です。Unicode 文字およびアンダースコアは使用しないでください。一般に、外部 DNS および公的 CA では、FQDN に非標準文字はサポートされていません (証明書で FQDN を SN に割り当てることが必要になります)。

