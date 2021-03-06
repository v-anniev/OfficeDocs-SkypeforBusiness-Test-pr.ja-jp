﻿---
title: 信頼済みアプリケーション サーバーの構成
TOCTitle: 信頼済みアプリケーション サーバーの構成
ms:assetid: 20c3815f-3048-4940-8c0f-cdfcd0801d5d
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204735(v=OCS.15)
ms:contentKeyID: 48271552
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 信頼済みアプリケーション サーバーの構成

 

_**トピックの最終更新日:** 2014-11-05_

混在環境で、新しい信頼済みアプリケーション サーバーを作成する場合は、Lync Server 2013 プールを次ホップ プールとして設定する必要があります。混在環境では、従来の Lync Server 2010 プールと Lync Server 2013 プールの両方がドロップダウン リストに表示されます。従来のプールを選択することはできません。

**信頼済みアプリケーション サーバーの作成時に Lync Server 2013 を次ホップとして選択する**

1.  トポロジ ビルダーを開きます。

2.  左側のウィンドウで、\[**信頼済みアプリケーション サーバー**\] を右クリックし、\[**新しい信頼済みアプリケーション プール**\] をクリックします。

3.  信頼済みアプリケーション プールの \[**プールの FQDN**\] を入力し、単一サーバーにするか複数サーバーにするかを選択します。

4.  その後、\[ **次へ** \] をクリックします。

5.  \[**次ホップの選択**\] ページで、ボックスの一覧から Lync Server 2013 フロントエンド プールを選択します。

6.  \[**完了**\] をクリックします。

7.  最上位の \[ **Lync Server**\] ノードを選択し、\[**操作**\] メニューの \[**公開**\] を選択します。
    
    **信頼済みアプリケーション プール**が正しく作成されていることと、適切なフロントエンド プールに関連付けられていることを確認します。

