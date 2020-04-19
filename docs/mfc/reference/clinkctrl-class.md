---
title: CLinkCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: 37d9e624c40f0d6aa7f3d3fa1ed3d97ffa478ee7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505703"
---
# <a name="clinkctrl-class"></a>CLinkCtrl クラス

Windows コモン SysLink コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CLinkCtrl:: CLinkCtrl](#clinkctrl)|`CLinkCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CLinkCtrl:: Create](#create)|リンクコントロールを作成し、 `CLinkCtrl`オブジェクトにアタッチします。|
|[CLinkCtrl::CreateEx](#createex)|拡張スタイルを使用してリンクコントロールを作成し、 `CLinkCtrl`オブジェクトにアタッチします。|
|[CLinkCtrl:: GetIdealHeight](#getidealheight)|リンクコントロールの理想的な高さを取得します。|
|[CLinkCtrl:: GetIdealSize](#getidealsize)|指定したリンクの幅に応じて、現在のリンクコントロールのリンクテキストの適切な高さを計算します。|
|[CLinkCtrl:: GetItem](#getitem)|リンクコントロール項目の状態と属性を取得します。|
|[CLinkCtrl:: GetItemID](#getitemid)|リンクコントロール項目の ID を取得します。|
|[CLinkCtrl:: GetItemState](#getitemstate)|リンクコントロール項目の状態を取得します。|
|[CLinkCtrl:: GetItemUrl](#getitemurl)|リンクコントロール項目によって表される URL を取得します。|
|[CLinkCtrl::HitTest](#hittest)|ユーザーが指定されたリンクをクリックしたかどうかを判断します。|
|[CLinkCtrl:: SetItem](#setitem)|リンクコントロール項目の状態と属性を設定します。|
|[CLinkCtrl:: SetItemID](#setitemid)|リンクコントロール項目の ID を設定します。|
|[CLinkCtrl:: SetItemState](#setitemstate)|リンクコントロール項目の状態を設定します。|
|[CLinkCtrl:: SetItemUrl](#setitemurl)|リンクコントロール項目によって表される URL を設定します。|

## <a name="remarks"></a>Remarks

"リンクコントロール" は、ハイパーテキストリンクをウィンドウに埋め込むための便利な方法を提供します。 実際のコントロールは、マークアップされたテキストを表示し、ユーザーが埋め込みリンクをクリックしたときに適切なアプリケーションを起動するウィンドウです。 1つのコントロール内で複数のリンクがサポートされており、0から始まるインデックスを使用してアクセスできます。

このコントロール (および`CLinkCtrl`クラス) は、Windows XP 以降で実行されているプログラムに対してのみ使用できます。

詳細については、Windows SDK の「 [Syslink Control](/windows/win32/Controls/syslink-overview) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

`CLinkCtrl` オブジェクトを構築します。

```
CLinkCtrl();
```

##  <a name="create"></a>  CLinkCtrl::Create

リンクコントロールを作成し、 `CLinkCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*lpszLinkMarkup*<br/>
表示するようにマークされたテキストを含む、0で終わる文字列へのポインター。 詳細については、「 [SysLink コントロールの概要](/windows/win32/Controls/syslink-overview)」の「マークアップとリンクアクセス」を参照してください。

*dwStyle*<br/>
リンクコントロールのスタイルを指定します。 コントロールスタイルの任意の組み合わせを適用します。 詳細については、 `Windows SDK` 「」の「[コモンコントロールスタイル](/windows/win32/Controls/common-control-styles)」を参照してください。

*rect*<br/>
リンクコントロールのサイズと位置を指定します。 これは、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/windows/win32/api/windef/ns-windef-rect)構造体のいずれかになります。

*pParentWnd*<br/>
リンクコントロールの親ウィンドウを指定します。 NULL にすることはできません。

*nID*<br/>
リンクコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

オブジェクトを構築`CLinkCtrl`するには、2つの手順を実行します。 まず、コンストラクターを呼び出し、次に`Create`を呼び出します。これにより、リンクコントロールが`CLinkCtrl`作成され、オブジェクトにアタッチされます。 拡張 windows スタイルをコントロールで使用する場合は、ではなく`Create` [CLinkCtrl:: CreateEx](#createex)を呼び出します。

2番目の形式`Create`のメソッドは非推奨とされます。 *Lpszlinkmarkup*パラメーターを指定する最初のフォームを使用します。

### <a name="example"></a>例

2つのリンクコントロールにアクセスするため`m_Link1`に`m_Link2`使用される、2つの変数を定義するコード例を次に示します。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、別のリンクコントロールの位置に基づいて1つのリンクコントロールを作成します。 アプリケーションの起動時に、リソースローダーによって最初のリンクコントロールが作成されます。 アプリケーションが OnInitDialog メソッドに入るときに、最初のリンクコントロールの位置を基準とする2番目のリンクコントロールを作成します。 次に、2番目のリンクコントロールのサイズを、表示されるテキストに合わせて変更します。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>  CLinkCtrl::CreateEx

拡張スタイルを使用してリンクコントロールを作成し、 `CLinkCtrl`オブジェクトにアタッチします。

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>パラメーター

*lpszLinkMarkup*<br/>
表示するようにマークされたテキストを含む、0で終わる文字列へのポインター。 詳細については、「 [SysLink コントロールの概要](/windows/win32/Controls/syslink-overview)」の「マークアップとリンクアクセス」を参照してください。

*dwExStyle*<br/>
リンクコントロールの拡張スタイルを指定します。 拡張 Windows スタイルの一覧については、Windows SDK の[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の*dwexstyle*パラメーターを参照してください。

*dwStyle*<br/>
リンクコントロールのスタイルを指定します。 コントロールスタイルの任意の組み合わせを適用します。 詳細については、「Windows SDK の[コモンコントロールスタイル](/windows/win32/Controls/common-control-styles)」を参照してください。

*rect*<br/>
リンクコントロールのサイズと位置を指定します。 これは、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/windows/win32/api/windef/ns-windef-rect)構造体のいずれかになります。

*pParentWnd*<br/>
リンクコントロールの親ウィンドウを指定します。 NULL にすることはできません。

*nID*<br/>
リンクコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

拡張`CreateEx` Windows スタイル定数を適用するには、 [Create](#create)の代わりにを使用します。

2番目の形式`CreateEx`のメソッドは非推奨とされます。 *Lpszlinkmarkup*パラメーターを指定する最初のフォームを使用します。

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

リンクコントロールの理想的な高さを取得します。

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>戻り値

コントロールの理想的な高さ (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)の動作を実装します。

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

指定したリンクの幅に応じて、現在のリンクコントロールのリンクテキストの適切な高さを計算します。

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*cxMaxWidth*|からリンクの最大幅 (ピクセル単位)。|
|入出力\* *pSize*|Windows の[サイズ](/windows/win32/api/windef/ns-windef-size)構造体へのポインター。 このメソッドから制御が戻るときに、 `SIZE`構造体の cy メンバーには、 *cxmaxwidth*によって指定されたリンクテキストの幅に対する理想的なリンクテキストの高さが含まれます。 構造体の*cx*メンバーには、実際に必要なリンクテキストの幅が含まれています。|

### <a name="return-value"></a>戻り値

リンクテキストの適切な高さ (ピクセル単位)。 戻り値は、 `SIZE`構造体の*cy*メンバーの値と同じです。

### <a name="remarks"></a>Remarks

`GetIdealSize`メソッドの例については、 [CLinkCtrl:: Create](#create)の例を参照してください。

このメソッドは、Windows SDK で説明されている[LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize)メッセージを送信します。

##  <a name="getitem"></a>  CLinkCtrl::GetItem

リンクコントロール項目の状態と属性を取得します。

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
項目情報を受け取る[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem)の動作を実装します。

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

リンクコントロール項目の ID を取得します。

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>パラメーター

*Ahsan*<br/>
リンクコントロール項目のインデックス。

*strID*<br/>
指定した項目の ID を格納している[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト。

*szID*<br/>
指定した項目の ID を格納している null で終わる文字列。

*cchID*<br/>
*Szid*バッファーのサイズ (文字数)。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

> [!NOTE]
>  この関数は、 *Szid または*MAX_LINKID_TEXT のバッファーが小さい場合にも FALSE を返します。

### <a name="remarks"></a>Remarks

特定のリンクコントロール項目の ID を取得します。 詳細については、Windows SDK の Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem)を参照してください。

##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState

リンクコントロール項目の状態を取得します。

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>パラメーター

*Ahsan*<br/>
リンクコントロール項目のインデックス。

*pnState*<br/>
指定された状態項目の値。

*stateMask*<br/>
取得する状態項目を記述するフラグの組み合わせ。 値の一覧については、 [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)構造体`state`のメンバーの説明を参照してください。 許容される項目は、で`state`許可されている項目と同じです。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

特定のリンクコントロール項目の指定された状態項目の値を取得します。 詳細については、Windows SDK の Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem)を参照してください。

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

リンクコントロール項目によって表される URL を取得します。

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>パラメーター

*Ahsan*<br/>
リンクコントロール項目のインデックス。

*strUrl*<br/>
指定した項目によって表される URL を含む[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト

*szUrl*<br/>
指定した項目によって表される URL を格納している null で終わる文字列。

*cchUrl*<br/>
*Szurl*バッファーのサイズ (文字数)。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

> [!NOTE]
>  この関数は、 *Szurl または strUrl*のバッファーが MAX_LINKID_TEXT より小さい場合にも FALSE を返します。

### <a name="remarks"></a>Remarks

指定されたリンクコントロール項目によって表される URL を取得します。 詳細については、Windows SDK の Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem)を参照してください。

##  <a name="hittest"></a>  CLinkCtrl::HitTest

ユーザーが指定されたリンクをクリックしたかどうかを判断します。

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>パラメーター

*phti*<br/>
ユーザーがクリック`LHITTESTINFO`したリンクに関する情報を格納している構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [LM_HITTEST](/windows/win32/Controls/lm-hittest)の動作を実装します。

##  <a name="setitem"></a>  CLinkCtrl::SetItem

リンクコントロール項目の状態と属性を設定します。

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
設定する情報を格納している[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem)の動作を実装します。

##  <a name="setitemid"></a>  CLinkCtrl::SetItemID

リンクコントロール項目の ID を取得します。

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>パラメーター

*Ahsan*<br/>
リンクコントロール項目のインデックス。

*szID*<br/>
指定した項目の ID を格納している null で終わる文字列。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

特定のリンクコントロール項目の ID を設定します。 詳細については、Windows SDK の Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem)を参照してください。

##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState

リンクコントロール項目の状態を取得します。

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>パラメーター

*Ahsan*<br/>
リンクコントロール項目のインデックス。

*pnState*<br/>
設定する指定された状態項目の値。

*stateMask*<br/>
設定する状態項目を説明するフラグの組み合わせ。 値の一覧については、 [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)構造体`state`のメンバーの説明を参照してください。 許容される項目は、で`state`許可されている項目と同じです。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

特定のリンクコントロール項目の指定された状態項目の値を設定します。 詳細については、Windows SDK の Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem)を参照してください。

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

リンクコントロール項目によって表される URL を設定します。

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>パラメーター

*Ahsan*<br/>
リンクコントロール項目のインデックス。

*szUrl*<br/>
指定した項目によって表される URL を格納している null で終わる文字列。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

指定されたリンクコントロール項目によって表される URL を設定します。 詳細については、Windows SDK の Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem)を参照してください。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)
