﻿---
title: 'Lync Server 2013: 電話会議、アプリケーションおよび仲介サーバーの QoS (Quality of Service) ポリシーの構成'
TOCTitle: 電話会議、アプリケーションおよび仲介サーバーの QoS (Quality of Service) ポリシーの構成
ms:assetid: 8adcbbc5-c9f5-476d-ab7f-72e61859cacf
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ205076(v=OCS.15)
ms:contentKeyID: 48272769
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 電話会議、アプリケーションおよび仲介サーバーの Lync Server 2013 における QoS (Quality of Service) ポリシーの構成

 

_**トピックの最終更新日:** 2014-06-23_

ポート範囲を構成すると、指定した種類のすべてのトラフィック (すべての音声トラフィックなど) が同じポート セットを通過するようになるため、サービス品質の使用が促進されます。これにより、システムは特定のパケットを簡単に識別およびマークできるようになります。ポート 49152 が音声トラフィック用に予約されている場合、ポート 49152 を通過するパケットは、これが音声パケットであることを示す DSCP コードでマークできます。さらに、これによりルーターはパケットを音声パケットとして識別し、マークされていないパケット (サーバーからサーバーへのファイルのコピーに使用されるパケットなど) よりも高い優先順位を指定できます。

ただし、ポートのセットを特定の種類のトラフィックに限定するだけでは、これらのポートを通過するパケットは適切な DSCP コードでマークされません。ポート範囲の定義に加えて、各ポート範囲に関連付ける DSCP コードを指定するサービス品質ポリシーを作成する必要もあります。Microsoft Lync Server 2013 の場合、これは通常 2 つのポリシー (音声用に 1 つとビデオ用に 1 つ) を作成することを意味します。

サービス品質ポリシーは、グループ ポリシーを使用すると最も簡単に作成および管理できます (これらの同じポリシーは、ローカル セキュリティ ポリシーを使用して作成することもできますが、そのためにはすべての各コンピューターで同じ手順を繰り返す必要があります)。QoS ポリシーの初期セット (音声用に 1 つとビデオ用に 1 つ) は、電話会議サーバー、アプリケーション サーバー、仲介サーバーなどのサービスを実行している Lync Server コンピューターにのみ適用する必要があります。これらすべてのコンピューターが同じ Active Directory OU に配置されている場合は、その OU に新しいグループ ポリシー オブジェクト (GPO) を割り当てるだけです。また、他の手順を実行して、新しいポリシーのターゲットを指定したコンピューターに設定することもできます。たとえば、セキュリティ グループに適切なコンピューターを配置し、グループ ポリシー セキュリティ フィルター処理を使用して、GPO をそのセキュリティ グループに適用できます。

音声管理用のサービス品質ポリシーを作成するには、グループ ポリシーの管理がインストールされているコンピューターにログオンします。\[グループ ポリシーの管理\] を開き (\[ **スタート** \] をクリックし、\[ **管理ツール** \] をポイントして \[ **グループ ポリシーの管理** \] をクリックします)、次の手順を実行します。

1.  \[グループ ポリシーの管理\] で、新しいポリシーを作成する必要のあるコンテナーを探します。たとえば、すべての Lync Server コンピューターが Lync Server という名前の OU にある場合は、新しいポリシーを Lync Server OU に作成する必要があります。

2.  適切なコンテナーを右クリックし、\[ **このドメインに GPO を作成し、このコンテナーにリンクする** \] をクリックします。

3.  \[ **新しい GPO** \] ダイアログ ボックスで、\[ **名前** \] ボックスに新しいグループ ポリシー オブジェクトの名前 (「**Lync Server QoS** 」など) を入力し、\[ **OK** \] をクリックします。

4.  新規に作成したポリシーを右クリックし、\[ **編集** \] をクリックします。

5.  グループ ポリシー管理エディターで、\[ **コンピューターの構成** \]、\[ **ポリシー** \]、\[ **Windows の設定** \] の順に展開し、\[ **ポリシー ベースの QoS** \] を右クリックして \[ **新規ポリシーの作成** \] をクリックします。

6.  \[ **ポリシー ベースの QoS** \] ダイアログ ボックスの最初のページで、\[ **名前** \] ボックスに新規ポリシーの名前 (「**Lync Server QoS** 」など) を入力します。\[ **DSCP 値を指定する** \] を選択し、値を **46** に設定します。\[ **出力方向のスロットル率を指定する** \] をオフのままにして、\[ **次へ** \] をクリックします。

7.  次のページで、\[**すべてのアプリケーション**\] が選択されていることを確認し、\[**次へ**\] をクリックします。これにより、すべてのアプリケーションが、指定した DSCP コードを持つ指定したポート範囲からのパケットに一致するようになります。

8.  3 番目のページで、\[**すべての発信元 IP アドレス\] と \[すべての宛先 IP アドレス**\] の両方が選択されていることを確認し、\[**次へ**\] をクリックします。この 2 つの設定により、これらのパケットを送信したコンピューター (IP アドレス) やこれらのパケットを受信するコンピューター (IP アドレス) にかかわらず、パケットが管理されます。

9.  4 番目のページで、\[ **この QoS ポリシーを適用するプロトコルを選択してください** \] ドロップダウン リストから \[ **TCP と UDP** \] を選択します。TCP (伝送制御プロトコル) と UDP (ユーザー データグラム プロトコル) は、Lync Server とそのクライアント アプリケーションで最もよく使用される 2 つのネットワーキング プロトコルです。

10. \[ **発信元ポート番号を指定してください** \] 見出しの下で、\[ **次の発信元ポート番号か範囲** \] をクリックします。付随するテキスト ボックスに、オーディオ送信用に予約されたポート範囲を入力します。たとえば、ポート 49152 からポート 57500 までを音声トラフィック用に予約した場合は、**49152:57500** という形式を使用してポート範囲を入力します。\[ **完了** \] をクリックします。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>46 の DSCP 値はある程度任意です。DSCP 46 は多くの場合に音声パケットのマーキングに使用されますが、音声通信に必ずしも DSCP 46 を使用する必要はありません。QoS を既に実装してあり、音声に別の DSCP コード (たとえば DSCP 40) を使用している場合は、その同じコードを使用 (つまり、音声に 40 を使用) するようにサービス品質ポリシーを構成する必要があります。通常は音声パケットのマーキングに DSCP 46 が使用されるため、サービス品質を実装したばかりの場合は、この値を音声に使用することをお勧めします。</td>
</tr>
</tbody>
</table>


音声トラフィックの QoS ポリシーを作成した後で、ビデオ トラフィック用の 2 つ目のポリシー (また、オプションでアプリケーション共有トラフィックの管理用の 3 つ目のポリシー) を作成する必要があります。ビデオのポリシーを作成するには、次の点を置き換えて、音声ポリシーの作成時に従ったのと同じ基本手順に従います。

  - 別の (一意の) ポリシー名 (**Lync Server ビデオ** など) を使用します。

  - DSCP 値を 46 ではなく **34** に設定します (34 の DSCP 値の使用は必須ではありません。要件は、音声に使用したのとは異なる DSCP 値をビデオに使用することだけです)。

  - ビデオ トラフィックには以前に構成したポート範囲を使用します。たとえば、ポート 57501 から 65535 までをビデオ用に予約した場合は、ポート範囲を **57501:65535** に設定します。

アプリケーション共有トラフィックの管理用のポリシーを作成する場合は、次の点を置き換えて 3 つ目のポリシーを作成する必要があります。

  - 別の (一意の) ポリシー名 (**Lync Server アプリケーション共有** など) を使用します。

  - DSCP 値を 46 ではなく **24** に設定します (この場合も、24 の DSCP 値の使用は必須ではありません。要件は、音声またはビデオに使用したのとは異なる DSCP 値をアプリケーション共有に使用することだけです)。

  - ビデオ トラフィックには以前に構成したポート範囲を使用します。たとえば、ポート 40803 から 49151 までをアプリケーション共有に予約した場合は、ポート範囲を **40803:49151** に設定します。

作成した新しいポリシーは、Lync Server コンピューターでグループ ポリシーが更新されるまで有効になりません。グループ ポリシーは自身を定期的に更新しますが、グループ ポリシーを更新する必要のある各コンピューターで次のコマンドを実行することにより、強制的に即時に更新できます。

    Gpupdate.exe /force

このコマンドは、Lync Server 管理シェルから、または管理者の資格情報で実行されている任意のコマンド ウィンドウから実行できます。管理者の資格情報でコマンド ウィンドウを実行するには、\[**スタート**\] ボタンをクリックして、\[**コマンド プロンプト**\] を右クリックし、\[**管理者として実行**\] をクリックします。

新しい QoS ポリシーが適用されたことを確認するには、次の手順を実行します。

1.  Lync Server コンピューターで、\[**スタート**\] ボタンをクリックし、\[**ファイル名を指定して実行**\] をクリックします。

2.  \[**ファイル名を指定して実行**\] ダイアログ ボックスで、「**regedit**」と入力し、Enter キーを押します。

3.  レジストリ エディターで、\[ **コンピューター** \]、\[ **HKEY\_LOCAL\_MACHINE** \]、\[ **SOFTWARE** \]、\[ **Policies** \]、\[ **Microsoft** \]、\[ **Windows** \] の順に展開し、\[ **QoS** \] をクリックします。\[ **QoS** \] に、作成した各 QoS ポリシーのレジストリ キーが表示されます。たとえば、2 つの新しいポリシー (Lync Server 音声 QoS という名前と Lync Server ビデオ QoS という名前) を作成した場合は、「Lync Server 音声 QoS」と「Lync Server ビデオ QoS」のレジストリ エントリが表示されます。

ネットワーク パケットが適切な DSCP 値でマークされるようにするには、次の手順を実行して、各コンピューターに新しいレジストリ エントリを作成する必要もあります。

1.  \[**スタート**\] ボタンをクリックし、\[**ファイル名を指定して実行**\] をクリックします。

2.  \[**ファイル名を指定して実行**\] ダイアログ ボックスで、「**regedit**」と入力し、Enter キーを押します。

3.  レジストリ エディターで、\[**HKEY\_LOCAL\_MACHINE**\]、\[**SYSTEM**\]、\[**CurrentControlSet**\]、\[**services**\]、\[**Tcpip**\] の順に展開します。

4.  \[ **Tcpip** \] を右クリックし、\[ **新規** \] をポイントして \[ **キー** \] をクリックします。新しいレジストリ キーを作成した後、「**QoS** 」と入力して Enter キーを押し、キーの名前を変更します。

5.  \[ **QoS** \] を右クリックし、\[ **新規** \] をポイントして \[ **文字列値** \] をクリックします。新しいレジストリ値を作成した後、「**NLA を使用しない** 」と入力して Enter キーを押し、キーの名前を変更します。

6.  \[ **NLA を使用しない** \] をダブルクリックします。\[ **文字列の編集** \] ダイアログ ボックスで、\[ **値データ** \] ボックスに「**1** 」と入力し、\[ **OK** \] をクリックします。

7.  レジストリ エディターを閉じて、コンピューターを再起動します。
