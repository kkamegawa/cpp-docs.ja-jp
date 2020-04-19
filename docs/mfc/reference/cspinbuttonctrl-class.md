---
title: CSpinButtonCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: c167745eed45b7081e62a2c3be225a33e7ee0520
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502444"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl クラス

Windows コモン スピン ボタン コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSpinButtonCtrl:: CSpinButtonCtrl](#cspinbuttonctrl)|`CSpinButtonCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|スピンボタンコントロールを作成し、 `CSpinButtonCtrl`オブジェクトにアタッチします。|
|[CSpinButtonCtrl::CreateEx](#createex)|指定された Windows 拡張スタイルを使用してスピンボタンコントロールを作成`CSpinButtonCtrl`し、オブジェクトにアタッチします。|
|[CSpinButtonCtrl:: GetAccel](#getaccel)|スピンボタンコントロールのアクセラレーション情報を取得します。|
|[CSpinButtonCtrl:: GetBase](#getbase)|スピンボタンコントロールの現在のベースを取得します。|
|[CSpinButtonCtrl:: GetBuddy](#getbuddy)|現在の関連ウィンドウへのポインターを取得します。|
|[CSpinButtonCtrl:: GetPos](#getpos)|スピンボタンコントロールの現在の位置を取得します。|
|[CSpinButtonCtrl::GetRange](#getrange)|スピンボタンコントロールの上限と下限 (範囲) を取得します。|
|[CSpinButtonCtrl::SetAccel](#setaccel)|スピンボタンコントロールのアクセラレーションを設定します。|
|[CSpinButtonCtrl::SetBase](#setbase)|スピンボタンコントロールのベースを設定します。|
|[CSpinButtonCtrl:: SetBuddy](#setbuddy)|スピンボタンコントロールの関連ウィンドウを設定します。|
|[CSpinButtonCtrl::SetPos](#setpos)|コントロールの現在の位置を設定します。|
|[CSpinButtonCtrl::SetRange](#setrange)|スピンボタンコントロールの上限と下限 (範囲) を設定します。|

## <a name="remarks"></a>Remarks

"スピンボタンコントロール" (アップダウンコントロールとも呼ばれます) とは、ユーザーがクリックして、スクロール位置やコンパニオンコントロールに表示される数値などの値を増減できる矢印ボタンのペアです。 スピンボタンコントロールに関連付けられている値は、現在の位置と呼ばれます。 スピンボタンコントロールは、"関連ウィンドウ" と呼ばれるコンパニオンコントロールで最もよく使用されます。

このコントロール (および`CSpinButtonCtrl`クラス) は、windows 95/98 および windows NT バージョン3.51 以降で実行されているプログラムに対してのみ使用できます。

ユーザーにとって、スピンボタンコントロールとその関連ウィンドウは、多くの場合、1つのコントロールのように見えます。 スピンボタンコントロールが関連ウィンドウの横に自動的に配置され、関連ウィンドウのキャプションが現在の位置に自動的に設定されるように指定できます。 スピンボタンコントロールとエディットコントロールを使用して、数値入力をユーザーに求めることができます。

上矢印をクリックすると、現在位置が最大値に移動し、下矢印をクリックすると現在位置が最小値に移動します。 既定では、最小値は100、最大値は0です。 最小設定値が最大値 (たとえば、既定の設定を使用する場合) よりも大きい場合は、上矢印をクリックすると位置の値が減少し、下矢印をクリックするとその値が大きくなります。

[連動] ウィンドウのないスピンボタンコントロールは、単純なスクロールバーの一種として機能します。 たとえば、タブコントロールにスピンボタンコントロールが表示され、ユーザーは追加のタブをスクロールして表示できる場合があります。

の使用方法`CSpinButtonCtrl`の詳細については、「 [Controls](../../mfc/controls-mfc.md) and [using CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

スピンボタンコントロールを作成し、 `CSpinButtonCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
スピンボタンコントロールのスタイルを指定します。 スピンボタンコントロールスタイルの任意の組み合わせをコントロールに適用します。 これらのスタイルは、Windows SDK の[アップダウンコントロールスタイル](/windows/win32/Controls/up-down-control-styles)で説明されています。

*rect*<br/>
スピンボタンコントロールのサイズと位置を指定します。 これは、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/previous-versions/dd162897\(v=vs.85\))構造体のいずれかになります。

*pParentWnd*<br/>
スピンボタンコントロールの親ウィンドウ (通常は`CDialog`) へのポインター。 NULL にすることはできません。

*nID*<br/>
スピンボタンコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

まず、2 `CSpinButtonCtrl`つの手順でオブジェクトを構築し、次にを呼び出し`Create`ます。これにより、スピンボタンコントロールが作成さ`CSpinButtonCtrl`れ、オブジェクトにアタッチされます。

拡張ウィンドウスタイルを使用してスピンボタンコントロールを作成するには、の`Create`代わりに[CSpinButtonCtrl:: CreateEx](#createex)を呼び出します。

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

コントロール (子ウィンドウ) を作成し、 `CSpinButtonCtrl`オブジェクトに関連付けます。

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
作成するコントロールの拡張スタイルを指定します。 拡張 windows スタイルの一覧については、Windows SDK の[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の*dwexstyle*パラメーターを参照してください。

*dwStyle*<br/>
スピンボタンコントロールのスタイルを指定します。 スピンボタンコントロールスタイルの任意の組み合わせをコントロールに適用します。 これらのスタイルは、Windows SDK の[アップダウンコントロールスタイル](/windows/win32/Controls/up-down-control-styles)で説明されています。

*rect*<br/>
*PParentWnd*のクライアント座標で、作成されるウィンドウのサイズと位置を記述する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
コントロールの親であるウィンドウへのポインター。

*nID*<br/>
コントロールの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

Windows `CreateEx`拡張スタイルの先頭 WS_EX_ によって指定された拡張 windows スタイルを適用するには、[[作成](#create)] ではなくを使用します。

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

`CSpinButtonCtrl` オブジェクトを構築します。

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

スピンボタンコントロールのアクセラレーション情報を取得します。

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>パラメーター

*nAccel*<br/>
*PAccel*によって指定された配列内の要素の数。

*pAccel*<br/>
アクセラレーション情報を受け取る[UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel)構造体の配列へのポインター。

### <a name="return-value"></a>戻り値

取得したアクセラレータ構造体の数。

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

スピンボタンコントロールの現在のベースを取得します。

```
UINT GetBase() const;
```

### <a name="return-value"></a>戻り値

現在の基本値。

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

現在の関連ウィンドウへのポインターを取得します。

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>戻り値

現在の関連ウィンドウへのポインター。

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

スピンボタンコントロールの現在の位置を取得します。

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>パラメーター

*lpbError*<br/>
値が正常に取得された場合は0に設定されたブール値へのポインター。エラーが発生した場合は0以外の値。 このパラメーターを NULL に設定した場合、エラーは報告されません。

### <a name="return-value"></a>戻り値

最初のバージョンは、下位ワードの16ビットの現在位置を返します。 エラーが発生した場合、上位ワードは0以外になります。

2番目のバージョンは、32ビットの位置を返します。

### <a name="remarks"></a>Remarks

返された値を処理するときに、コントロールは、関連ウィンドウのキャプションに基づいて現在の位置を更新します。 関連するウィンドウがない場合、またはキャプションに無効な値または範囲外の値が指定されている場合、コントロールはエラーを返します。

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

スピンボタンコントロールの上限と下限 (範囲) を取得します。

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>パラメーター

*方*<br/>
コントロールの下限を受け取る整数への参照。

*上限*<br/>
コントロールの上限を受け取る整数への参照。

### <a name="return-value"></a>戻り値

最初のバージョンでは、上限と下限を含む32ビットの値が返されます。 下位ワードはコントロールの上限であり、上位の単語は下限の値になります。

### <a name="remarks"></a>Remarks

このメンバー関数`GetRange32`は、スピンボタンコントロールの範囲を32ビット整数として取得します。

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

スピンボタンコントロールのアクセラレーションを設定します。

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>パラメーター

*nAccel*<br/>
*PAccel*によって指定された[UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel)構造体の数。

*pAccel*<br/>
アクセラレーション情報を格納している UDACCEL 構造体の配列へのポインター。 要素は、 `nSec`メンバーに基づいて昇順に並べ替える必要があります。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

スピンボタンコントロールのベースを設定します。

```
int SetBase(int nBase);
```

### <a name="parameters"></a>パラメーター

*nBase*<br/>
コントロールの新しい基本値。 10進数の場合は10、16進数の場合は16になります。

### <a name="return-value"></a>戻り値

成功した場合は前のベース値。無効なベースが指定されている場合は0。

### <a name="remarks"></a>Remarks

基本値は、関連ウィンドウが10進数または16進数の数字を表示するかどうかを決定します。 16進数値は常に符号なしです。10進数には符号が付きます。

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

スピンボタンコントロールの関連ウィンドウを設定します。

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>パラメーター

*pWndBuddy*<br/>
新しい関連ウィンドウへのポインター。

### <a name="return-value"></a>戻り値

前の関連ウィンドウへのポインター。

### <a name="remarks"></a>Remarks

スピンコントロールは、ほとんどの場合、一部のコンテンツを表示する、エディットコントロールなどの別のウィンドウに関連付けられています。 この他のウィンドウは、スピンコントロールの "関連" と呼ばれます。

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

スピンボタンコントロールの現在の位置を設定します。

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
コントロールの新しい位置。 この値は、コントロールの上限と下限によって指定された範囲内である必要があります。

### <a name="return-value"></a>戻り値

前の位置 (の場合は16ビット`SetPos`有効桁数、の`SetPos32`場合は32ビット精度)。

### <a name="remarks"></a>Remarks

`SetPos32`32ビットの位置を設定します。

##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange

スピンボタンコントロールの上限と下限 (範囲) を設定します。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>パラメーター

*Nlower*と*nlower*<br/>
コントロールの上限と下限。 で`SetRange`は、どちらの制限も UD_MAXVAL より大きくすることも、UD_MINVAL より小さくすることもできません。また、2つの制限の差は UD_MAXVAL を超えることはできません。 `SetRange32`制限はありません。任意の整数を使用します。

### <a name="remarks"></a>Remarks

このメンバー関数`SetRange32`は、スピンボタンコントロールの32ビット範囲を設定します。

> [!NOTE]
>  スピンボタンの既定の範囲は、最大値がゼロ (0)、最小値が100に設定されています。 最大値は最小値よりも小さいため、上矢印をクリックすると位置が減少し、下矢印をクリックするとその位置が増加します。 これら`CSpinButtonCtrl::SetRange`の値を調整するには、を使用します。

## <a name="see-also"></a>関連項目

[MFC のサンプル CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl クラス](../../mfc/reference/csliderctrl-class.md)
