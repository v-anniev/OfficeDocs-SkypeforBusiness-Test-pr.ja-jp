﻿---
title: スマート カード認証へのユーザーの登録
TOCTitle: スマート カード認証へのユーザーの登録
ms:assetid: a6445a83-a94b-423f-ba2a-12b5f84c5d75
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn308570(v=OCS.15)
ms:contentKeyID: 56270131
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# スマート カード認証へのユーザーの登録

 

_**トピックの最終更新日:** 2016-12-08_

スマート カードの認証を行うユーザーを登録する方法は、主に 2 つあります。Web 登録を使ってスマート カード認証のユーザーを直接登録する方法がより簡単で、登録エージェントを使う方法はより複雑です。このトピックでは、スマート カードの証明書を自分で登録する方法について説明します。

ユーザーの代わりに登録エージェントとして登録する方法の詳細については、「他のユーザーの代理で証明書を登録する」 ([http://go.microsoft.com/fwlink/p/?LinkID=313367](http://go.microsoft.com/fwlink/p/?linkid=313367)) を参照してください。

## スマート カードの認証を行うユーザーを登録するには、次の操作を行います。

1.  Lync が有効なユーザーの資格情報を使って、Windows 8 ワークステーションにログインします。

2.  Internet Explorer を起動します。

3.  **証明機関 Web 登録**のページ (例: https://MyCA.contoso.com/certsrv) を開きます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Internet Explorer 10 を使っている場合は、この Web サイトを互換モードで見る必要がある場合があります。</td>
    </tr>
    </tbody>
    </table>


4.  Web サイトの \[**ようこそ**\] ページで、\[**証明書の要求**\] を選びます。

5.  次に、\[**証明書の要求の詳細設定**\] を選びます。

6.  \[**この CA への要求を作成し送信する。**\] を選びます。

7.  \[**証明書のテンプレート**\] セクションで \[**スマート カード ユーザー**\] を選び、\[証明書の要求の詳細設定\] を次のように入力します。
    
      - \[**キーのオプション**\] で次の設定を確認します。
        
          - \[**新しいキー セットを作成する**\] ラジオ ボタンを選ぶ
        
          - \[**CSP**\] で、\[**Microsoft ベース スマート カード暗号化プロバイダー**\] を選ぶ
        
          - \[**キー使用法**\] で、\[**Exchange**\] を選ぶ (このオプションのみ有効)
        
          - \[**キーのサイズ**\] に、**2048** と入力する
        
          - \[**自動キー コンテナー名**\] が選択されている
        
          - その他のボックスはオフにします。
    
      - \[**追加オプション**\] で次の値を確認します。
        
          - \[**要求の形式**\] で \[**CMC**\] を選ぶ。
        
          - \[**ハッシュ アルゴリズム**\] で \[**sha1**\] を選ぶ。
        
          - \[**フレンドリ名**\] に **Smardcard Certificate** と入力する。

8.  物理カード リーダーを使っている場合は、デバイスにスマート カードを挿入します。

9.  \[**送信**\] をクリックして証明書要求を送信します。

10. 入力を求められたら、仮想スマート カードを作成したときに使った PIN を入力します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>仮想スマート カードの既定の PIN の値は、「12345678」です。</td>
    </tr>
    </tbody>
    </table>


11. 証明書が発行されたら、\[**この証明書のインストール**\] をクリックして登録プロセスを完了します。
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>「証明書の要求の生成はこの Web ブラウザーではサポートされていません。」というエラーが発生して証明書の作成が失敗した場合、解決する方法として次の 3 つが考えられます。
    <ol>
    <li><p>Internet Explorer の [互換表示] を有効にする</p></li>
    <li><p>Internet Explorer で [イントラネットの設定を有効にする] オプションを有効にする</p></li>
    <li><p>Internet Explorer の [インターネット オプション] の [セキュリティー] タブで、[すべてのゾーンを既定のレベルにリセットする] を選ぶ</p></li>
    </ol></td>
    </tr>
    </tbody>
    </table>
