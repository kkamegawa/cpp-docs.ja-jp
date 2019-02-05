---
title: CHotKeyCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 0b673c873f773844c13894d3f0448536f297dc53
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894511"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl クラス

Windows コモン ホット キー コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|`CHotKeyCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|ホット キー コントロールを作成し、それにアタッチします、`CHotKeyCtrl`オブジェクト。|
|[CHotKeyCtrl::CreateEx](#createex)|指定された Windows の拡張スタイルでホット キー コントロールを作成しにアタッチします、`CHotKeyCtrl`オブジェクト。|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|ホット キー コントロールのホット キーの仮想キー コードと修飾フラグを取得します。|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|ホット キーに割り当てられている、ローカルの文字セットで、キー名を取得します。|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|キー名を指定した仮想キー コードに割り当てられている、ローカルの文字セットを取得します。|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|ホット キー コントロールのホット キーの組み合わせを設定します。|
|[CHotKeyCtrl::SetRules](#setrules)|無効な組み合わせとホット キー コントロールの既定の修飾子の組み合わせを定義します。|

## <a name="remarks"></a>Remarks

「ホット キー コントロール」は、ユーザーは、ホット キーを作成できるウィンドウです。 「ホット キー」は、操作をすばやく実行するユーザーが押すキーの組み合わせです。 (たとえば、ユーザー作成できますを特定のウィンドウをアクティブ化し、Z オーダーの一番上にホット キー)。ホット キー コントロールでは、ユーザーの選択を表示し、ユーザーが有効なキーの組み合わせを選択することにより、します。

このコントロール (つまり、`CHotKeyCtrl`クラス) は以降、Windows 95/98 および Windows NT version 3.51 で実行するプログラムにのみ使用できます。

ユーザーがキーの組み合わせを選択した場合、アプリケーションはコントロールから、指定したキーの組み合わせを取得し、WM_SETHOTKEY メッセージを使用して、システムで、ホット キーを設定します。 押されたときに、ホット キー、その後、システムの任意の部分から WM_SETHOTKEY メッセージで指定されたウィンドウは SC_HOTKEY を指定する位置であるメッセージを受信します。 このメッセージには、受信するウィンドウがアクティブにします。 ホット キーは WM_SETHOTKEY 終了と呼ばれるアプリケーションまで有効です。

このメカニズムは WM_HOTKEY メッセージと、Windows に依存する、ホット キーのサポートと異なる[RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey)と[UnregisterHotKey](/windows/desktop/api/winuser/nf-winuser-unregisterhotkey)関数。

使用しての詳細については`CHotKeyCtrl`を参照してください[コントロール](../../mfc/controls-mfc.md)と[を使用して CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="chotkeyctrl"></a>  CHotKeyCtrl::CHotKeyCtrl

`CHotKeyCtrl` オブジェクトを構築します。

```
CHotKeyCtrl();
```

##  <a name="create"></a>  CHotKeyCtrl::Create

ホット キー コントロールを作成し、それにアタッチします、`CHotKeyCtrl`オブジェクト。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
ホット キー コントロールのスタイルを指定します。 コントロールのスタイルの任意の組み合わせを適用します。 参照してください[コモン コントロール スタイル](/windows/desktop/Controls/common-control-styles)詳細については、Windows sdk。

*rect*<br/>
ホット キー コントロールのサイズと位置を指定します。 いずれかのことができます、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT 構造体](/windows/desktop/api/windef/ns-windef-tagrect)します。

*pParentWnd*<br/>
通常、ホット キー コントロールの親ウィンドウを指定します、 [CDialog](../../mfc/reference/cdialog-class.md)します。 NULL は指定できません。

*nID*<br/>
ホット キー コントロールの ID を指定します

### <a name="return-value"></a>戻り値

0 以外の場合、初期化が成功した場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

構築する、 `CHotKeyCtrl` 2 つのステップ内のオブジェクト。 最初に、コンス トラクターを呼び出すし、呼び出して`Create`、ホット キー コントロールを作成しにアタッチする`CHotKeyCtrl`オブジェクト。

コントロールで拡張ウィンドウ スタイルを使用する場合は、呼び出す[CreateEx](#createex)の代わりに`Create`します。

##  <a name="createex"></a>  CHotKeyCtrl::CreateEx

コントロール (子ウィンドウ) を作成し、それをするには、この関数を呼び出して、`CHotKeyCtrl`オブジェクト。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwExStyle*<br/>
作成されるコントロールの拡張スタイルを指定します。 拡張 Windows スタイルの一覧は、次を参照してください。、 *dwExStyle*パラメーターを[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK に含まれています。

*dwStyle*<br/>
ホット キー コントロールのスタイルを指定します。 コントロールのスタイルの任意の組み合わせを適用します。 詳細については、次を参照してください。[コモン コントロール スタイル](/windows/desktop/Controls/common-control-styles)Windows SDK に含まれています。

*rect*<br/>
参照を[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)のクライアント座標で、作成するには、ウィンドウの位置とサイズを記述する構造体*pParentWnd*します。

*pParentWnd*<br/>
コントロールの親であるウィンドウへのポインター。

*nID*<br/>
コントロールの子ウィンドウ ID

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

使用`CreateEx`の代わりに[作成](#create)、Windows の拡張スタイルの先頭で指定された、Windows の拡張スタイルを適用する**WS_EX**します。

##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey

ホット キー コントロールのキーボード ショートカットの仮想キー コードと修飾フラグを取得します。

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>パラメーター

*wVirtualKeyCode*<br/>
[out]キーボード ショートカットの仮想キー コード。 標準の仮想キー コードの一覧は、Winuser.h を参照してください。

*と*<br/>
[out]キーボード ショートカット キーの修飾子キーを示すフラグのビットごとの組み合わせ (OR)。

修飾フラグは次のとおりです。

|フラグ|対応するキー|
|----------|-----------------------|
|HOTKEYF_ALT|ALT キー|
|HOTKEYF_CONTROL|CTRL キー|
|HOTKEYF_EXT|拡張キー|
|HOTKEYF_SHIFT|Shift キー|

### <a name="return-value"></a>戻り値

最初のオーバー ロードされたメソッド、仮想キー コードと修飾フラグを含む DWORD。 下位ワードの下位バイトが仮想キー コードが含まれています、下位ワードの高位バイトには、修飾子のフラグが含まれています。 上位ワードは 0 です。

### <a name="remarks"></a>Remarks

仮想キー コードと修飾子キーを同時に、キーボード ショートカットを定義します。

##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName

ホット キーのローカライズされた名前を取得するには、このメンバー関数を呼び出します。

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>戻り値

現在選択されているホット キーのローカライズされた名前。 選択したホット キーがない場合`GetHotKeyName`空の文字列を返します。

### <a name="remarks"></a>Remarks

このメンバー関数によって返される名前のキーボード ドライバーに由来します。 キーボードのローカライズされていないドライバーをインストールするには、Windows のローカライズされたバージョンで、またはその逆です。

##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName

指定した仮想キー コードに割り当てられているキーのローカライズされた名前を取得するには、このメンバー関数を呼び出します。

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>パラメーター

*vk*<br/>
仮想キー コード。

*fExtended*<br/>
仮想キー コードが拡張キー、TRUE の場合それ以外の場合は FALSE です。

### <a name="return-value"></a>戻り値

指定されたキーのローカライズされた名前、 *vk*パラメーター。 キーがマップの名前を持たない場合`GetKeyName`空の文字列を返します。

### <a name="remarks"></a>Remarks

この関数によって返されるキーの名前は、Windows のローカライズ版でローカライズされていないキーボード ドライバーをインストールできるように、キーボード ドライバーから、その逆です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>  CHotKeyCtrl::SetHotKey

ホット キー コントロールのキーボード ショートカットを設定します。

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>パラメーター

*wVirtualKeyCode*<br/>
[in]キーボード ショートカットの仮想キー コード。 標準の仮想キー コードの一覧は、Winuser.h を参照してください。

*と*<br/>
[in]キーボード ショートカット キーの修飾子キーを示すフラグのビットごとの組み合わせ (OR)。

修飾フラグは次のとおりです。

|フラグ|対応するキー|
|----------|-----------------------|
|HOTKEYF_ALT|ALT キー|
|HOTKEYF_CONTROL|CTRL キー|
|HOTKEYF_EXT|拡張キー|
|HOTKEYF_SHIFT|Shift キー|

### <a name="remarks"></a>Remarks

仮想キー コードと修飾子キーを同時に、キーボード ショートカットを定義します。

##  <a name="setrules"></a>  CHotKeyCtrl::SetRules

無効な組み合わせとホット キー コントロールの既定の修飾子の組み合わせを定義するには、この関数を呼び出します。

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>パラメーター

*wInvalidComb*<br/>
無効なキーの組み合わせを指定するフラグの配列。 次の値の組み合わせを指定できます。

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE 変更されていないキー

- HKCOMB_S シフト

- HKCOMB_SA SHIFT + ALT

- CTRL + HKCOMB_SC シフト

- HKCOMB_SCA SHIFT + CTRL + ALT

*と*<br/>
ユーザーが、無効な組み合わせを入力するときに使用するキーの組み合わせを指定するフラグの配列。 修飾フラグの詳細については、次を参照してください。 [GetHotKey](#gethotkey)します。

### <a name="remarks"></a>Remarks

ユーザーが無効なキーの組み合わせに入ったときに指定されたフラグで定義されている*wInvalidComb*、システムで指定されたフラグで、ユーザーが入力したキーの組み合わせ、OR 演算子を使用する*と*. 結果として得られるキーの組み合わせは文字列に変換し、ホット キー コントロールに表示されます。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)

