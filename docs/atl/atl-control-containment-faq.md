---
title: 'ATL コントロール コンテインメント : Q & A 集'
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 42f9b41b99e13fcfe2fb003acb348c9464e0fd05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223319"
---
# <a name="atl-control-containment-faq"></a>ATL コントロール コンテインメント : Q & A 集

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>ATL クラスは、ActiveX コントロール サポートを容易にしますか。

ATL のコントロール ホスト コードで、ATL クラスを使用する必要がありません。単に作成することができます、 **"AtlAxWin80**ウィンドウと必要な場合、コントロール ホスト API を使用 (詳細については、次を参照してください。 **ATL コントロール ホスト API とは**します。 ただし、次のクラス包含機能を使いやすきます。

|クラス|説明|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|ラップ、 **"AtlAxWin80**ウィンドウで、ウィンドウの作成、コントロールの作成や、ウィンドウへのコントロールおよびホスト オブジェクトのインターフェイス ポインターを取得するメソッドを指定できます。|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|ラップする **"AtlAxWinLic80"** ウィンドウで、ウィンドウの作成、コントロールの作成や、ウィンドウへのライセンス付きコントロールおよびホスト オブジェクトのインターフェイス ポインターを取得するメソッドを指定できます。|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|ダイアログ リソースに基づく ActiveX コントロール クラスの基本クラスとして機能します。 このようなコントロールは、他の ActiveX コントロールを含めることができます。|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|ダイアログ リソースに基づくダイアログ クラスの基本クラスとして機能します。 このようなダイアログ ボックスは、ActiveX コントロールを含めることができます。|
|[CWindow](../atl/reference/cwindow-class.md)|メソッドを提供します。 [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)、そのホスト ウィンドウの ID を指定し、コントロールのインターフェイス ポインターが返されます。 さらに、Windows API のラッパーをによって公開されている`CWindow`通常、ウィンドウの管理を容易にします。|

## <a name="what-is-the-atl-control-hosting-api"></a>新機能、ATL コントロール ホスト API でしょうか。

ATL のコントロール ホスト API は、ActiveX コントロール コンテナーとして機能する任意のウィンドウを許可する一連の関数。 これらの関数は静的または動的にソース コードとして利用できるため、プロジェクトにリンクされている、ATL90.dll によって公開されています。 コントロール ホスト関数は、次の表に表示されます。

|関数|説明|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|ホスト オブジェクトを作成し、指定のウィンドウに接続し、既存のコントロールをアタッチします。|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|ホスト オブジェクトを作成する、指定のウィンドウに接続し、コントロールを読み込みます。|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|ライセンスされた ActiveX コントロールを作成し、それを初期化し、指定したウィンドウでホスト[して](reference/composite-control-global-functions.md#atlaxcreatecontrol)します。|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|ホスト オブジェクトを作成し、指定のウィンドウに接続し、コントロールを読み込みます (イベント シンクを設定するのには、許可も)。|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|ライセンスされた ActiveX コントロールを作成し、それを初期化し、指定したウィンドウでホスト[して](reference/composite-control-global-functions.md#atlaxcreatecontrollic)します。|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|ダイアログ リソースからモードレス ダイアログ ボックスを作成し、ウィンドウ ハンドルを返します。|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|ダイアログ リソースからモーダル ダイアログ ボックスを作成します。|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|返します、 **IUnknown**ウィンドウでホストされるコントロールのインターフェイス ポインター。|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|返します、 **IUnknown**ウィンドウに接続されているホスト オブジェクトのインターフェイス ポインター。|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|コントロール ホスト コードを初期化します。|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|コントロール ホスト コードは初期化されません。|

`HWND`最初の 3 つの関数のパラメーターは (ほとんど) すべての種類の既存のウィンドウである必要があります。 これら 3 つの関数のいずれかに明示的に呼び出す場合 (通常は、する必要はありません)、ホストとして既に動作しているウィンドウを識別するハンドルを渡さないでください (この場合、既存のホスト オブジェクト解放されない)。

最初の 7 つの関数を呼び出す[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)暗黙的にします。

> [!NOTE]
>  コントロール ホスト API では、ActiveX コントロール サポートの ATL のサポートの基礎を形成します。 ただし、活用または ATL のラッパー クラスを最大限に活用する場合、これらの関数を直接呼び出す必要はほとんどありませんが、通常は。 詳細については、次を参照してください。[する ATL クラスを容易に ActiveX コントロール コンテインメント](which-atl-classes-facilitate-activex-control-containment-q.md)します。

## <a name="what-is-atlaxwin100"></a>AtlAxWin100 とは何ですか。

`AtlAxWin100` ATL のコントロール ホスト機能を提供できるウィンドウ クラスの名前です。 このクラスのインスタンスを作成するときにウィンドウ プロシージャは自動的に使用されているウィンドウに関連付けられているホスト オブジェクトを作成し、ウィンドウのタイトルとして指定したコントロールに読み込み、コントロール ホスト API を使用します。

## <a name="when-do-i-need-to-call-atlaxwininit"></a>ときに AtlAxWinInit を呼び出す必要があるのでしょうか。

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)登録、 **"AtlAxWin80**ウィンドウ (さらに、いくつかのカスタム ウィンドウ メッセージには) クラスのため、ホスト ウィンドウを作成する前に、この関数を呼び出す必要があります。 ただし、Api (およびそれらを使用するクラス) をホストから明示的に、この関数を呼び出す必要はありません常を多くの場合、この関数を呼び出します。 この関数を複数回呼び出しても弊害はありません。

## <a name="what-is-a-host-object"></a>ホスト オブジェクトとは何ですか。

ホスト オブジェクトは、特定のウィンドウに、ATL によって提供される ActiveX コントロール コンテナーを表す COM オブジェクトです。 ホスト オブジェクトはサブクラス コンテナー ウィンドウ コントロールにメッセージを反映したもの、コントロールで使用するために必要なコンテナー インターフェイスを提供および公開できるように、 [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)と[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)インターフェイス コントロールの環境を構成するようにします。

ホスト オブジェクトを使用して、コンテナーのアンビエント プロパティを設定することができます。

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>1 つのウィンドウでは、複数のコントロールをホストできますか。

単一の ATL ホスト ウィンドウには、複数のコントロールをホストすることはできません。 各ホスト ウィンドウは (これはメッセージのリフレクションとコントロールごとのアンビエント プロパティを処理するための単純なメカニズムの許可) 時に正確に 1 つのコントロールを保持するために設計されています。 ただし、1 つのウィンドウで複数のコントロールを表示するユーザーが必要な場合は、そのウィンドウの子として複数のホスト ウィンドウを作成すると簡単です。

## <a name="can-i-reuse-a-host-window"></a>ホスト ウィンドウを再利用できますか。

ホストの windows を再利用することは推奨されません。 コードの堅牢性を確保するには、1 つのコントロールの有効期間に、ホスト ウィンドウの有効期間を関連付ける必要があります。

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>ときに AtlAxWinTerm を呼び出す必要があるのでしょうか。

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)の登録を解除、 **"AtlAxWin80**ウィンドウ クラス。 既存のすべてのホスト ウィンドウが破棄された後に、(ホスト ウィンドウの作成が不要になった) 場合に、この関数を呼び出す必要があります。 この関数を呼び出さない場合、ウィンドウ クラスは登録解除する自動的にプロセスが終了します。

## <a name="hosting-activex-controls-using-atl-axhost"></a>ATL AXHost を使用して ActiveX コントロールのホスト

このセクションのサンプルでは、AXHost を作成する方法とさまざまな ATL 関数を使用して ActiveX コントロールをホストする方法を示します。 コントロールとシンク イベントにアクセスする方法も示します (を使用して[IDispEventImpl](../atl/reference/idispeventimpl-class.md)) ホストされているコントロールから。 このサンプルでは、メイン ウィンドウ、または子ウィンドウには、予定表コントロールをホストします。

定義に注目してください、`USE_METHOD`シンボル。 1 ~ 8 で変更するには、この記号の値を変更することができます。 シンボルの値は、コントロールの作成方法を決定します。

- 値が偶数`USE_METHOD`ホストのサブクラスを作成するには、ウィンドウへの呼び出し、コントロールのホストに変換します。 奇数の値は、コードは、ホストとして機能する子ウィンドウを作成します。

- 値が`USE_METHOD`コントロールへのアクセスを 1 および 4 の場合は、間ともホストを作成する呼び出しで行われます。 イベントのシンク。 5 ~ 8 の値は、ホストにインターフェイスを照会し、シンクをフックします。

次に概要を示します。

|USE_METHOD|ホスト|アクセスを制御し、イベント シンク|使用する関数|
|-----------------|----------|--------------------------------------|---------------------------|
|1|子ウィンドウ|1 つのステップ|CreateControlLicEx|
|2|メイン ウィンドウ|1 つのステップ|AtlAxCreateControlLicEx|
|3|子ウィンドウ|1 つのステップ|CreateControlEx|
|4|メイン ウィンドウ|1 つのステップ|AtlAxCreateControlEx|
|5|子ウィンドウ|複数のステップ|CreateControlLic|
|6|メイン ウィンドウ|複数のステップ|AtlAxCreateControlLic|
|7|子ウィンドウ|複数のステップ|CreateControl|
|9|メイン ウィンドウ|複数のステップ|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>関連項目

[コントロール コンテインメント:](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T クラス](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowLic インターフェイス](../atl/reference/iaxwinhostwindowlic-interface.md)
