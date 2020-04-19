---
title: イベントの追加 (ATL チュートリアル、パート 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: c9a7c6f38a2f47ec808081e440a200737ad1928a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127575"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>イベントの追加 (ATL チュートリアル、パート 5)

この手順では、`ClickIn` と `ClickOut` イベントを ATL コントロールに追加します。 ユーザーが多角形内をクリックすると `ClickIn` イベントが発生し、ユーザーが外側をクリックすると `ClickOut` が発生します。 イベントを追加するタスクは次のとおりです。

- `ClickIn` メソッドと `ClickOut` メソッドの追加

- タイプライブラリの生成

- コネクションポイントインターフェイスの実装

## <a name="adding-the-clickin-and-clickout-methods"></a>ClickIn メソッドと ClickOut メソッドの追加

手順 2. で ATL コントロールを作成したときに、[**接続ポイント**] チェックボックスをオンにしました。 これにより、Polygon .idl ファイルに `_IPolyCtlEvents` インターフェイスが作成されました。 インターフェイス名はアンダースコアで始まります。 これは、インターフェイスが内部インターフェイスであることを示すための規則です。 したがって、COM オブジェクトを参照できるプログラムは、インターフェイスをユーザーに表示しないことを選択できます。 また、**接続ポイント**を選択すると、Polygon ファイルに次の行が追加され、`_IPolyCtlEvents` が既定のソースインターフェイスであることが示されることにも注意してください。

`[default, source] dispinterface _IPolyCtlEvents;`

Source 属性は、コントロールが通知のソースであることを示しているので、コンテナーでこのインターフェイスを呼び出します。

ここで、`ClickIn` および `ClickOut` メソッドを `_IPolyCtlEvents` インターフェイスに追加します。

### <a name="to-add-the-clickin-and-clickout-methods"></a>ClickIn メソッドと ClickOut メソッドを追加するには

1. **ソリューションエクスプローラー**で、Polygon を開き、PolygonLib ライブラリの `dispInterface_IPolyCtlEvents` 宣言の `methods:` に次のコードを追加します。

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn` メソッドと `ClickOut` メソッドは、クリックされたポイントの x 座標と y 座標をパラメーターとして受け取ります。

## <a name="generating-the-type-library"></a>タイプライブラリの生成

この時点でタイプライブラリを生成します。これは、プロジェクトが、接続ポイントインターフェイスと、コントロールの接続ポイントコンテナーインターフェイスを構築するために必要な情報を取得するために使用するためです。

### <a name="to-generate-the-type-library"></a>タイプライブラリを生成するには

1. プロジェクトをリビルドします。

     - または -

1. **ソリューションエクスプローラー**で Polygon ファイルを右クリックし、ショートカットメニューの [**コンパイル**] をクリックします。

これにより、タイプライブラリである Polygon .tlb ファイルが作成されます。 Polygon ファイルはバイナリファイルであり、直接表示または編集できないため、**ソリューションエクスプローラー**からは参照できません。

## <a name="implementing-the-connection-point-interfaces"></a>コネクションポイントインターフェイスの実装

コントロールの接続ポイントインターフェイスと接続ポイントコンテナーインターフェイスを実装します。 COM では、コネクションポイントのメカニズムによってイベントが実装されます。 COM オブジェクトからイベントを受信するために、コンテナーは COM オブジェクトが実装するコネクションポイントへのアドバイザリコネクションを確立します。 COM オブジェクトは複数のコネクションポイントを持つことができるため、COM オブジェクトは接続ポイントコンテナーインターフェイスも実装します。 コンテナーは、このインターフェイスを使用して、サポートされているコネクションポイントを特定できます。

コネクションポイントを実装するインターフェイスは `IConnectionPoint`と呼ばれ、接続ポイントコンテナーを実装するインターフェイスは `IConnectionPointContainer`と呼ばれます。

`IConnectionPoint`を実装するには、接続ポイントの実装ウィザードを使用します。 このウィザードでは、タイプライブラリを読み取り、起動可能な各イベントに対して関数を実装することによって、`IConnectionPoint` インターフェイスを生成します。

### <a name="to-implement-the-connection-points"></a>接続ポイントを実装するには

1. **ソリューションエクスプローラー**で _IPolyCtlEvents_CP を開き、`CProxy_IPolyCtlEvents` クラスの `public:` ステートメントの下に次のコードを追加します。

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

このファイルには、`IConnectionPointImpl`から派生した `CProxy_IPolyCtlEvents` というクラスがあることがわかります。 _IPolyCtlEvents_CP では、2つのメソッド `Fire_ClickIn` と `Fire_ClickOut`を定義しています。これは2つの座標パラメーターを受け取ります。 コントロールからイベントを発生させる場合は、これらのメソッドを呼び出します。

[**接続ポイント**を使用してコントロールを作成する] オプションを選択すると、_IPolyCtlEvents_CP .h ファイルが生成されます。 また、`CProxy_PolyEvents` と `IConnectionPointContainerImpl` をコントロールの複数の継承リストに追加し、適切なエントリを COM マップに追加することによって `IConnectionPointContainer` を公開しました。

イベントをサポートするためのコードの実装が完了しました。 ここで、適切な時点でイベントを発生させるコードをいくつか追加します。 ユーザーがコントロールでマウスの左ボタンをクリックしたときに、`ClickIn` または `ClickOut` イベントが発生することに注意してください。 ユーザーがボタンをクリックしたことを確認するには、`WM_LBUTTONDOWN` メッセージのハンドラーを追加します。

### <a name="to-add-a-handler-for-the-wm_lbuttondown-message"></a>WM_LBUTTONDOWN メッセージのハンドラーを追加するには

1. **クラスビュー**で、`CPolyCtl` クラスを右クリックし、ショートカットメニューの [**プロパティ**] をクリックします。

1. [**プロパティ**] ウィンドウで、[**メッセージ**] アイコンをクリックし、左側の一覧の [`WM_LBUTTONDOWN`] をクリックします。

1. 表示されるドロップダウン リストから、クリックして **\<追加 > OnLButtonDown** します。 `OnLButtonDown` ハンドラー宣言が Polyctl.htm に追加され、ハンドラーの実装が Polyctl.htm に追加されます。

次に、ハンドラーを変更します。

### <a name="to-modify-the-onlbuttondown-method"></a>OnLButtonDown メソッドを変更するには

1. Polyctl.htm の `OnLButtonDown` メソッドを構成するコードを変更します (ウィザードによって配置されたすべてのコードを削除します)。次のようになります。

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

このコードでは、`OnDraw` 関数で計算されたポイントを使用して、`PtInRegion`への呼び出しによってユーザーのマウスクリックを検出する領域を作成します。

*Umsg*パラメーターは、処理される Windows メッセージの ID です。 これにより、一連のメッセージを処理する1つの関数を使用できます。 *WParam*および*lParam*パラメーターは、処理されるメッセージの標準値です。 パラメーター *Bhandled*を使用すると、関数がメッセージを処理するかどうかを指定できます。 既定では、この値は、関数がメッセージを処理したことを示すために TRUE に設定されますが、FALSE に設定することもできます。 これにより、メッセージを送信する別のメッセージハンドラー関数の検索が ATL によって続行されます。

## <a name="building-and-testing-the-control"></a>コントロールのビルドとテスト

次に、イベントを試してみましょう。 コントロールをビルドし、ActiveX コントロールテストコンテナーを再び開始します。 今度は、[イベントログ] ウィンドウを表示します。 イベントを出力ウィンドウにルーティングするには、[**オプション**] メニューの [ログ**記録**] をクリックし、[**出力ウィンドウにログ記録する**] を選択します。 コントロールを挿入し、ウィンドウ内をクリックしてみます。 `ClickIn` は、塗りつぶされた多角形内をクリックすると起動され、外側をクリックすると `ClickOut` が発生することに注意してください。

次に、プロパティページを追加します。

[手順 4 に戻る](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [手順 6 に進む](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>関連項目

[チュートリアル](../atl/active-template-library-atl-tutorial.md)
