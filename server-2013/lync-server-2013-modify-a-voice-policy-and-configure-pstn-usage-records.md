﻿---
title: Lync Server 2013 での音声ポリシーの変更と PSTN 使用法レコードの構成
TOCTitle: Lync Server 2013 での音声ポリシーの変更と PSTN 使用法レコードの構成
ms:assetid: 6c53aaf5-218b-4bd4-8cea-31bc9d53f1bd
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398511(v=OCS.15)
ms:contentKeyID: 48272437
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での音声ポリシーの変更と PSTN 使用法レコードの構成

 

_**トピックの最終更新日:** 2012-11-01_

音声ポリシーを変更する場合は、次の手順に従います。 新しい音声ポリシーを作成する場合は、「[Lync Server 2013 での音声ポリシーの作成と PSTN 使用法レコードの構成](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)」の手順を参照してください。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>公衆交換電話網 (PSTN) 使用法レコードが関連付けられていない音声ポリシーに割り当てられているユーザーは、通話を発信できません。エンタープライズ VoIP 展開で利用できるすべての PSTN 使用法レコードの一覧とそれぞれのプロパティを表示するには、「<a href="lync-server-2013-view-pstn-usage-records.md">Lync Server 2013 での PSTN 使用法レコードの表示</a>」を参照してください。</td>
</tr>
</tbody>
</table>


## 音声ポリシーを変更するには

1.  RTCUniversalServerAdmins グループのメンバーとして、あるいは CsVoiceAdministrator、CsServerAdministrator、または CsAdministrator の役割のメンバーとしてコンピューターにログオンします。詳細については、「[Lync Server 2013 でのセットアップのアクセス許可の委任](lync-server-2013-delegate-setup-permissions.md)」を参照してください。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**音声ルーティング**\] をクリックし、\[**音声ポリシー**\] をクリックします。

4.  \[**音声ポリシー**\] ページで、音声ポリシー名をダブルクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>スコープと名前は、音声ポリシーの作成時に設定されています。 これらは変更できません。</td>
    </tr>
    </tbody>
    </table>


5.  (オプション) \[**音声ポリシーの編集**\] に、音声ポリシーの説明情報を追加で入力します。

6.  次のチェック ボックスをオンまたはオフにして、\[**通話機能**\] をそれぞれ有効または無効にします。
    
      - \[**ボイス メールのエスケープ**\] は、同時呼び出しが構成されていて、携帯電話がオフになっている、バッテリーが切れている、または圏外になっている場合に、通話が即座にユーザーの携帯電話のボイス メール システムに転送されないようにします。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>この機能は、Lync Server 管理シェルからのみ構成できます。</td>
        </tr>
        </tbody>
        </table>
    
      - \[**着信の転送**\] では、他の電話機やクライアント デバイスに通話を転送できます。Lync Server 2013 には、着信の転送に関する構成オプションが極めて幅広く用意されています。たとえば、着信が外部で PSTN に転送されることを組織が許可しない方針の場合、管理者は特殊な音声ポリシーを適用して、この制限を展開することができます。既定では有効です。
    
      - \[**委任**\] では、代わりに通話を送受信する他のユーザーを指定できます。Lync Server 2013 では、代理人が同時呼び出しを構成できます。同時呼び出しを使用すると、マネージャーに対して着信があった場合に、代理人によって設定されたターゲット ユーザー全員が同時に呼び出されます。この機能を使用すると、代理人はマネージャーに対する直接の着信により柔軟に対応できます。既定では有効です。
    
      - **\[通話の転送\]** では、他のユーザーに通話を転送できます。 既定では有効です。
    
      - \[**コール パーク**\] では、通話を保留 (パーク) し、別の電話機やクライアントで受けることができます。既定では無効です。
    
      - \[**同時呼び出し**\] では、追加の電話機 (携帯電話など) や他のエンドポイント デバイスで、着信の呼び出し音を鳴らすことができます。Lync Server 2013 には、同時呼び出しに関する構成オプションが極めて幅広く用意されています。既定では有効です。
    
      - **\[チーム呼び出し\]** では、定義したチームのユーザーがチームの他のメンバーの呼び出しに応答できます。 既定では有効です。
    
      - \[**PSTN 再ルート**\] では、WAN が混雑していたり利用できない場合に、このポリシーを割り当てられているユーザーが他のエンタープライズ ユーザーに掛けた通話を、公衆交換電話網 (PSTN) で再ルートできます。既定では有効です。
    
      - **\[帯域幅ポリシーの上書き\]** では、特定のユーザーに対する通話受付管理 (CAC) ポリシーの決定を、管理者が上書きできます。 既定では無効です。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>ポリシーが上書きされるのはユーザーに着信する通話のみです。ユーザーが発信する通話は上書きされません。セッションの確立後、使用帯域幅は正確に記録されます。この設定は慎重に使用してください。</td>
        </tr>
        </tbody>
        </table>
    
      - \[**悪意のある通話のトレース**\] では、ユーザーがクライアントの UI を使用して、悪意のある通話 (爆弾脅迫など) を報告できます。報告されると、通話詳細記録 (CDR) 内のその通話にフラグが付けられます。既定では無効です。

7.  この音声ポリシーの PSTN 使用法レコードの関連付けと構成を行うには、次のいずれかを実行します。
    
      - エンタープライズ VoIP 展開で利用できるすべての PSTN 使用法レコードの一覧から 1 つ以上のレコードを選択するには、\[**選択**\] をクリックします。この音声ポリシーに関連付けるレコードを選択状態にし、\[**OK**\] をクリックします。
    
      - PSTN 使用法レコードをこの音声ポリシーから削除するには、レコードを選択状態にして \[**削除**\] をクリックします。
    
      - 新しい PSTN 使用法レコードを定義してこの音声ポリシーに関連付けるには、次の操作を実行します。
        
        1.  \[**新規**\] をクリックします。
        
        2.  \[**名前**\] フィールドに、レコードを説明する一意の名前を入力します。たとえば、Redmond で勤務しているフルタイム従業員用に **Redmond** という名前の PSTN 使用法レコードを作成し、パートタイム従業員用に **RedmondTemps** という名前の別のレコードを作成することができます。
            
            <table>
            <thead>
            <tr class="header">
            <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
            </tr>
            </thead>
            <tbody>
            <tr class="odd">
            <td>PSTN 使用法レコードの名前は、エンタープライズ VoIP 展開内で一意である必要があります。 レコードの保存後、[<strong>名前</strong>] フィールドを編集することはできません。</td>
            </tr>
            </tbody>
            </table>
        
        3.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
            
              - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から 1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
            
              - PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
            
              - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
            
              - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
        
        4.  \[**OK**\] をクリックします。
    
      - この音声ポリシーに既に関連付けられている PSTN 使用法レコードを編集するには、次の操作を実行します。
        
        1.  編集する PSTN 使用法レコードを選択状態にし、\[**詳細の表示**\] をクリックします。
        
        2.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
            
              - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から 1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
            
              - この PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
            
              - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
            
              - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
        
        3.  \[**OK**\] をクリックします。

8.  最適なパフォーマンスを得るために、PSTN 使用法レコードを並べ替えます。 一覧内でのレコードの位置を変更するには、レコードの名前を選択状態にして、上矢印または下矢印をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>音声ポリシーの PSTN 使用法レコードの一覧の順序は重要です。 Lync Server はこの一覧を上から下へ検索します。 この一覧は、使用頻度の高い順番に並べておくことを推奨します。たとえば、 &quot;レドモンド市内&quot;、&quot;レドモンド長距離&quot;、&quot;レドモンド国際&quot;、&quot;レドモンド バックアップ&quot; の順に並べます。</td>
    </tr>
    </tbody>
    </table>


9.  この音声ポリシーの着信の転送および同時呼び出しに対する PSTN 使用法レコードの関連付けと構成を行うには、次のいずれかを実行します。
    
      - この音声ポリシーと同じ PSTN 使用法レコードを着信の転送と同時呼び出しに使用する場合は、ドロップダウン メニューから \[**呼び出し PSTN 使用法を使用したルーティング**\] を選択します。
    
      - 内部の Lync ユーザーのみに着信の転送と同時呼び出しを許可する場合は、ドロップダウン メニューから \[**内部 Lync ユーザーのみへのルーティング**\] を選択します。通話は外部の PSTN 番号には転送されません。
    
      - この音声ポリシーに使用されているのとは別の PTSN 使用法レコードを着信の転送と同時呼び出しに指定する場合は、ドロップダウン メニューから \[**カスタムの PSTN 使用法を使用したルーティング**\] を選択します。このオプションを選択するとコントロールが表示され、着信の転送と同時呼び出しに対して、既存の PSTN 使用法レコードを選択するかまたは新しい PSTN 使用法レコードを作成できます。
        
          - 着信の転送と同時呼び出しのために PSTN 使用法レコードの一覧から 1 つ以上のレコードを選択するには、\[**選択**\] をクリックします。この着信の転送と同時呼び出しのポリシーに関連付けるレコードを選択状態にし、\[**OK**\] をクリックします。
        
          - この着信の転送と同時呼び出しのポリシーから PSTN 使用法レコードを削除するには、レコードを選択状態にして \[**削除**\] をクリックします。
        
          - 新しい PSTN 使用法レコードを定義してこの着信の転送と同時呼び出しのポリシーに関連付けるには、次の操作を実行します。
            
            1.  \[**新規**\] をクリックします。
            
            2.  \[**名前**\] フィールドに、レコードを説明する一意の名前を入力します。
                
                <table>
                <thead>
                <tr class="header">
                <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
                </tr>
                </thead>
                <tbody>
                <tr class="odd">
                <td>PSTN 使用法レコードの名前は、エンタープライズ VoIP 展開内で一意である必要があります。レコードの保存後、[<strong>名前</strong>] フィールドを編集することはできません。</td>
                </tr>
                </tbody>
                </table>
            
            3.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
                
                  - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から 1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
                
                  - PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
                
                  - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
                
                  - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
            
            4.  \[**OK**\] をクリックします。
        
          - この音声ポリシーに既に関連付けられている PSTN 使用法レコードを編集するには、次の操作を実行します。
            
            1.  編集する PSTN 使用法レコードを選択状態にし、\[**詳細の表示**\] をクリックします。
            
            2.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
                
                  - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から、1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
                
                  - この PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
                
                  - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
                
                  - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
            
            3.  \[**OK**\] をクリックします。

10. (オプション) 音声ポリシーをテストする番号を入力して、\[**実行**\] をクリックします。テスト結果は、\[**テストする変換後の番号**\] の下に表示されます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>まだテストに成功していない音声ポリシーを保存して、後で再構成することができます。詳細については、「<a href="lync-server-2013-test-voice-routing.md">Lync Server 2013 での音声ルーティングのテスト</a>」を参照してください。</td>
    </tr>
    </tbody>
    </table>


11. \[**OK**\] をクリックします。

12. \[**音声ポリシー**\] ページで \[**確定**\] をクリックし、\[**すべて確定**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>音声ポリシーを作成または変更したときは常に、[<strong>すべて確定</strong>] コマンドを実行して、構成の変更を公開する必要があります。詳細については、「操作」のドキュメントの「<a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013 での音声ルーティング構成に対する保留中の変更の公開</a>」を参照してください。</td>
    </tr>
    </tbody>
    </table>


13. (オプション) \[ボイス メールのエスケープ\] で、ユーザーの携帯電話のボイス メールが通話に即座に応答したことを検出して、携帯電話のボイス メールへの通話を切断するように設定できます。これにより、通話はユーザーの他のエンドポイントで呼び出しを続行できるため、ユーザーが通話に応答できます。ボイス メール ポリシーの構成方法の詳細については、「展開」のドキュメントの「[Lync Server 2013 でのボイス メール エスケープの構成](lync-server-2013-configuring-voice-mail-escape.md)」を参照してください。

## 関連項目

#### タスク

[Lync Server 2013 での音声ポリシーの作成と PSTN 使用法レコードの構成](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Lync Server 2013 での PSTN 使用法レコードの表示](lync-server-2013-view-pstn-usage-records.md)  
[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)  
[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)  
[Lync Server 2013 での音声ルーティング構成に対する保留中の変更の公開](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  
[Lync Server 2013 でのボイス メール エスケープの構成](lync-server-2013-configuring-voice-mail-escape.md)  

#### その他のリソース

[Lync Server 2013 での音声ルーティングのテスト](lync-server-2013-test-voice-routing.md)
