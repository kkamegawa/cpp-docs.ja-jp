---
title: CBitmapButton クラス
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: 45e0214cafb80c3e00a7e888a3170040f46113f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388463"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton クラス

ラベルがテキストではなくビットマップ イメージのプッシュ ボタン コントロールを作成します。

## <a name="syntax"></a>構文

```
class CBitmapButton : public CButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|`CBitmapButton` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|ダイアログ ボックスのボタンのオブジェクトに関連付けます、`CBitmapButton`クラス、名前で、ビットマップを読み込むし、ビットマップに合わせてボタンのサイズします。|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|アプリケーションのリソース ファイルから 1 つまたは複数の名前付きのビットマップ リソースを読み込み、ビットマップをオブジェクトにアタッチして、オブジェクトを初期化します。|
|[CBitmapButton::SizeToContent](#sizetocontent)|ビットマップに合わせてボタンをサイズします。|

## <a name="remarks"></a>Remarks

`CBitmapButton` オブジェクトに含める最大 4 つのビットマップは、ボタンのさまざまな状態の画像が含まれる: 最新 (または通常) 下 (または選択した)、フォーカスが設定され、無効にします。 最初のビットマップのみが必要です。その他はオプションです。

ビットマップ ボタンのイメージには、イメージ自体と同様に、イメージの周りの境界線が含まれます。 罫線は、通常、ボタンの状態の表示中に役割を果たします。 たとえば、フォーカスがある状態のビットマップは、状態が、境界線または境界の太い実線の四角形の破線埋め込みのような通常は。 ビットマップ、無効な状態は、通常に似ています、1 つの状態が、低コントラスト (淡色表示のメニューの選択) など。

任意のサイズでは、これらのビットマップを指定できますが、場合の状態を表すビットマップと同じサイズと同様に扱わすべてれます。

さまざまなアプリケーションでは、ビットマップ イメージのさまざまな組み合わせを要求します。

|上へ|[下へ移動]|フォーカスされている|無効|アプリケーション|
|--------|----------|-------------|--------------|-----------------|
|×||||ビットマップ|
|×|×|||WS_TABSTOP スタイル ボタンをクリックします。|
|×|×|×|×|すべての状態を持つダイアログ ボタン|
|×|×|×||WS_TABSTOP スタイルでダイアログ ボタン|

ビットマップ ボタン コントロールを作成する場合は、ボタンがオーナー描画を指定する BS_OWNERDRAW スタイルを設定します。 これにより、ボタンのため、WM_DRAWITEM メッセージを送信する Windowsフレームワークでは、これらのメッセージを処理しのボタンの外観を管理します。

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>ウィンドウのクライアント領域で、ビットマップ ボタン コントロールを作成するには

1. ボタンの 1 ~ 4 個のビットマップ イメージを作成します。

1. 構築、 [CBitmapButton](#cbitmapbutton)オブジェクト。

1. 呼び出す、[作成](../../mfc/reference/cbutton-class.md#create)関数を Windows のボタン コントロールを作成し、アタッチ先、`CBitmapButton`オブジェクト。

1. 呼び出す、 [LoadBitmaps](#loadbitmaps)メンバー関数は、ビットマップのボタンを構築した後のビットマップ リソースを読み込めません。

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>ダイアログ ボックスに、ビットマップ ボタン コントロールを含める

1. ボタンの 1 ~ 4 個のビットマップ イメージを作成します。

1. オーナー描画ボタン、[ビットマップ] ボタンを配置するダイアログ テンプレートを作成します。 テンプレート内のボタンのサイズを指定することはありません。

1. ボタンのキャプションを"MYIMAGE"などの値に設定し、IDC_MYIMAGE などのボタンのシンボルを定義します。

1. アプリケーションのリソース スクリプトには、"X"(、フォーカスが設定および無効になっています) ためのボタンのキャプションに使用される文字列に手順 3 またはの各ボタンの文字"U""D""F"のいずれかの追加によって構築された ID を作成したイメージを与えます。 ボタンのキャプション"MYIMAGE"では、たとえば、Id になります"MYIMAGEU"、"MYIMAGED、""MYIMAGEF、"と「手順 3.」 **する必要があります**二重引用符で囲まれた、ビットマップの ID を指定します。 それ以外の場合リソース エディターは、リソースに整数値を割り当てるし、イメージの読み込み時に、MFC は失敗します。

1. アプリケーションのダイアログ クラスで (から派生した`CDialog`)、追加、`CBitmapButton`メンバー オブジェクトです。

1. `CDialog`オブジェクトの[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)ルーチンを呼び出し、`CBitmapButton`オブジェクトの[AutoLoad](#autoload)関数は、ボタンのコントロール ID をパラメーターとして使用して、`CDialog`オブジェクト**this**ポインター。

BN_CLICKED などの Windows 通知メッセージを処理する場合、その親にビットマップ ボタン コントロールから送信 (から派生したクラスは、通常`CDialog`)、追加、 `CDialog`-派生オブジェクトをメッセージ マップ エントリとメッセージ ハンドラー メンバー各メッセージの関数。 によって送信された通知を`CBitmapButton`オブジェクトは、によって送信されたものと同じ、 [CButton](../../mfc/reference/cbutton-class.md)オブジェクト。

クラスは、 [CToolBar](../../mfc/reference/ctoolbar-class.md)ビットマップのボタンに別のアプローチを採用します。

詳細については`CBitmapButton`を参照してください[コントロール](../../mfc/controls-mfc.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="autoload"></a>  CBitmapButton::AutoLoad

ダイアログ ボックスのボタンのオブジェクトに関連付けます、`CBitmapButton`クラス、名前で、ビットマップを読み込むし、ビットマップに合わせてボタンのサイズします。

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
ボタンのコントロールの id。

*pParent*<br/>
ボタンを所有するオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

使用して、`AutoLoad`ビットマップ ボタンとして ダイアログ ボックスのオーナー描画ボタンを初期化します。 この関数を使用する手順については、の「解説」には、`CBitmapButton`クラス。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

##  <a name="cbitmapbutton"></a>  CBitmapButton::CBitmapButton

`CBitmapButton` オブジェクトを作成します。

```
CBitmapButton();
```

### <a name="remarks"></a>Remarks

C++ で作成した後`CBitmapButton`オブジェクト、呼び出す[CButton::Create](../../mfc/reference/cbutton-class.md#create) Windows ボタン コントロールを作成してに接続する、`CBitmapButton`オブジェクト。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

##  <a name="loadbitmaps"></a>  CBitmapButton::LoadBitmaps

リソースの名前または ID 番号、または使用できない場合を識別するビットマップ画像をロードするときに、この関数を使用して、`AutoLoad`のため、たとえば、ダイアログ ボックスの一部ではないビットマップ ボタンを作成する機能します。

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>パラメーター

*lpszBitmapResource*<br/>
または「を」状態の通常のビットマップ ボタンのビットマップの名前を含む null で終わる文字列へのポインター。 必須。

*lpszBitmapResourceSel*<br/>
または「停止」状態のビットマップ ボタンの選択は、ビットマップの名前を含む null で終わる文字列へのポインター。 NULL にすることがあります。

*lpszBitmapResourceFocus*<br/>
ビットマップ ボタンのビットマップの名前を含む null で終わる文字列へのポインターには、状態が重点を置いています。 NULL にすることがあります。

*lpszBitmapResourceDisabled*<br/>
ビットマップ ボタンのビットマップの名前を含む null で終わる文字列へのポインターには、状態が無効になります。 NULL にすることがあります。

*nIDBitmapResource*<br/>
ビットマップ リソースのビットマップ ボタンの通常の状態「を」リソースの ID 番号を指定します。 必須。

*nIDBitmapResourceSel*<br/>
ビットマップのボタンの選択または「停止」状態は、ビットマップ リソースのリソース ID 番号を指定します。 0 にすることがあります。

*nIDBitmapResourceFocus*<br/>
フォーカスのある状態のビットマップ リソースのリソース ID 番号を指定します。 0 にすることがあります。

*nIDBitmapResourceDisabled*<br/>
ビットマップ ボタンの無効の状態のビットマップ リソースのリソース ID 番号を指定します。 0 にすることがあります。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

##  <a name="sizetocontent"></a>  CBitmapButton::SizeToContent

ビットマップのサイズをビットマップ ボタンのサイズを変更するには、この関数を呼び出します。

```
void SizeToContent();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプル CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton クラス](../../mfc/reference/cbutton-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
