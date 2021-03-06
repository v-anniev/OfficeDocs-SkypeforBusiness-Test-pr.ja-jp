﻿---
title: Lync Server ユーザーの検索
TOCTitle: Lync Server ユーザーの検索
ms:assetid: 3b9f6f55-d7a9-46ae-8e10-f221ba0d3bb5
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg429701(v=OCS.15)
ms:contentKeyID: 48271830
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server ユーザーの検索

 

_**トピックの最終更新日:** 2014-05-14_

検索クエリの結果を使用して、Lync Server 2013 のユーザーを構成できます。ユーザーは、表示名、名、姓、セキュリティ アカウント マネージャー (SAM) のアカウント名、SIP アドレス、または回線 URI (Uniform Resource Identifier) で検索できます。

ユーザーの検索には、Lync Server コントロール パネルまたは Active Directory ユーザーおよびコンピューター スナップインを使用できます。次の手順では、Lync Server コントロール パネルを使用してユーザーを検索する方法について説明します。

> [!NOTE]
> 中央フォレスト トポロジを含む環境では、ユーザーの電子メール アドレスでユーザーを検索すると、検索結果が正確でなくなる可能性があります。代わりに、SIP アドレスのプレフィックス (たとえば、sip:name) を指定してユーザーを検索し、検索フィルターを追加し、電子メール アドレスの一部を含む SIP アドレスを選択することができます。また、<strong>Get-CSUser</strong> コマンドレットを使用することもできます。


## 1 つ以上のユーザーを検索するには

1.  CsUserAdministrator または CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**ユーザー** \] をクリックします。

4.  \[**ユーザーの検索** \] ボックスに、検索対象のユーザー アカウントの表示名、名、姓、SAM のアカウント名、SIP アドレス、または回線 URI の全体か最初の一部の文字列を入力して、\[**検索** \] をクリックします。

5.  (オプション) 結果を絞り込むための追加の検索条件を次のように指定します。
    
    1.  画面の右上隅、\[**検索結果** \] の上にある展開の矢印ボタンをクリックして、\[**フィルターの追加** \] をクリックします。
    
    2.  ユーザーのプロパティを入力するか、ドロップダウン リストの矢印をクリックして選択し、ユーザーのプロパティを指定します。
    
    3.  \[**次の値に等しい** \] リストで、\[**次の値に等しい** \] または \[**次の値に等しくない** \] をクリックします。
    
    4.  テキスト ボックスで、検索結果のフィルターに使う検索条件を入力して、\[**検索** \] をクリックします。

6.  \[**検索結果** \] に検索結果が表示されます。リストのユーザーの一部または全部を選択して、選択したユーザーに対して構成タスクを実行できます。

## 関連項目

#### その他のリソース

[Lync Server 2013 で有効なユーザー アカウント情報の表示](lync-server-2013-viewing-information-about-user-accounts-enabled-for-lync-server.md)  
[Lync Server 2013 のユーザーの有効化または無効化](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

