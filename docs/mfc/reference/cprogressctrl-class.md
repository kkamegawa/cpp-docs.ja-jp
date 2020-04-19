---
title: CProgressCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: 9d63a1113e521eb73c99c47b335eb7ab00ccd753
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502852"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl クラス

Windows コモン プログレス バー コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|`CProgressCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CProgressCtrl::Create](#create)|プログレスバーコントロールを作成し、 `CProgressCtrl`オブジェクトにアタッチします。|
|[CProgressCtrl::CreateEx](#createex)|指定された Windows 拡張スタイルを使用してプログレスコントロールを作成`CProgressCtrl`し、オブジェクトにアタッチします。|
|[CProgressCtrl::GetBarColor](#getbarcolor)|現在の進行状況バーコントロールのプログレスインジケーターバーの色を取得します。|
|[CProgressCtrl::GetBkColor](#getbkcolor)|現在の進行状況バーの背景色を取得します。|
|[CProgressCtrl::GetPos](#getpos)|プログレスバーの現在位置を取得します。|
|[CProgressCtrl::GetRange](#getrange)|プログレスバーコントロールの範囲の下限と上限を取得します。|
|[CProgressCtrl::GetState](#getstate)|現在の進行状況バーコントロールの状態を取得します。|
|[CProgressCtrl::GetStep](#getstep)|現在の進行状況バーコントロールのプログレスバーの増分値を取得します。|
|[CProgressCtrl::OffsetPos](#offsetpos)|プログレスバーコントロールの現在位置を指定されたインクリメントだけ進め、新しい位置を反映するようにバーを再描画します。|
|[CProgressCtrl::SetBarColor](#setbarcolor)|現在の進行状況バーコントロールのプログレスインジケーターバーの色を設定します。|
|[CProgressCtrl::SetBkColor](#setbkcolor)|プログレスバーの背景色を設定します。|
|[CProgressCtrl::SetMarquee](#setmarquee)|現在の進行状況バーコントロールに対してマーキーモードをオンまたはオフにします。|
|[CProgressCtrl::SetPos](#setpos)|プログレスバーコントロールの現在位置を設定し、新しい位置を反映するようにバーを再描画します。|
|[CProgressCtrl::SetRange](#setrange)|プログレスバーコントロールの範囲の最小値と最大値を設定し、新しい範囲を反映するようにバーを再描画します。|
|[CProgressCtrl::SetState](#setstate)|現在の進行状況バー コントロールの状態を設定します。|
|[CProgressCtrl:: SetStep](#setstep)|プログレスバーコントロールのステップインクリメントを指定します。|
|[CProgressCtrl::StepIt](#stepit)|プログレスバーコントロールの現在位置をステップごとに進めます (「 [Setstep](#setstep)」を参照)。新しい位置を反映するようにバーを再描画します。|

## <a name="remarks"></a>Remarks

進行状況バーコントロールは、時間のかかる操作の進行状況を示すためにアプリケーションで使用できるウィンドウです。 操作の進行に合わせてシステムの強調表示色を使用して、左から右に徐々に入力される四角形で構成されます。

プログレスバーコントロールには、範囲と現在位置があります。 この範囲は操作の合計期間を表し、現在の位置は、アプリケーションが操作の完了に向けた進行状況を表します。 ウィンドウプロシージャは、範囲と現在位置を使用して、強調表示色で塗りつぶすプログレスバーの割合を決定します。 範囲と現在位置の値は符号付き整数として表現されるため、現在の位置の値の有効範囲は-2147483648 ~ 2147483647 です。

の使用方法`CProgressCtrl`の詳細については、「 [Controls](../../mfc/controls-mfc.md) and [using CProgressCtrl](../../mfc/using-cprogressctrl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl

`CProgressCtrl` オブジェクトを構築します。

```
CProgressCtrl();
```

### <a name="remarks"></a>Remarks

`CProgressCtrl`オブジェクトを構築した後`CProgressCtrl::Create` 、を呼び出して進行状況バーコントロールを作成します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>  CProgressCtrl::Create

プログレスバーコントロールを作成し、 `CProgressCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
プログレスバーコントロールのスタイルを指定します。 次のプログレスバーコントロールスタイルに加えて、Windows SDK の[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)で説明されているウィンドウスタイルの任意の組み合わせをコントロールに適用します。

- PBS_VERTICAL では、進行状況に関する情報が、上から下に縦方向に表示されます。 このフラグがない場合、進行状況バーコントロールは水平方向に左から右に表示されます。

- PBS_SMOOTH は、進行状況バーコントロールに徐々に滑らかに入力して表示します。 このフラグが設定されていない場合、コントロールはブロックで塗りつぶされます。

*rect*<br/>
プログレスバーコントロールのサイズと位置を指定します。 これは、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/previous-versions/dd162897\(v=vs.85\))構造体のいずれかになります。 コントロールは子ウィンドウである必要があるため、指定された座標は*pParentWnd*のクライアント領域に対して相対的になります。

*pParentWnd*<br/>
プログレスバーコントロールの親ウィンドウ (通常は`CDialog`) を指定します。 NULL にすることはできません。

*nID*<br/>
プログレスバーコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

オブジェクトが正常`CProgressCtrl`に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

オブジェクトを構築`CProgressCtrl`するには、2つの手順を実行します。 まず、コンストラクターを呼び出して`CProgressCtrl`オブジェクトを作成し、を呼び出し`Create`ます。これにより、進行状況バーコントロールが作成されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>  CProgressCtrl::CreateEx

コントロール (子ウィンドウ) を作成し、 `CProgressCtrl`オブジェクトに関連付けます。

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
作成するコントロールの拡張スタイルを指定します。 拡張 Windows スタイルの一覧については、Windows SDK の[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の*dwexstyle*パラメーターを参照してください。

*dwStyle*<br/>
プログレスバーコントロールのスタイルを指定します。 Windows SDK の[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)で説明されているウィンドウスタイルの任意の組み合わせを適用します。

*rect*<br/>
*PParentWnd*のクライアント座標で、作成されるウィンドウのサイズと位置を記述する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
コントロールの親であるウィンドウへのポインター。

*nID*<br/>
コントロールの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

Windows `CreateEx`拡張スタイルの先頭**WS_EX_** によって指定された拡張 windows スタイルを適用するには、[[作成](#create)] ではなくを使用します。

##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor

現在の進行状況バーコントロールのプログレスインジケーターバーの色を取得します。

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>戻り値

現在の進行状況バーの色 ( [COLORREF](/windows/win32/gdi/colorref)値として表される)、またはプログレスインジケーターバーの色が既定の色の場合は CLR_DEFAULT。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor)メッセージを送信します。

##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor

現在の進行状況バーの背景色を取得します。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>戻り値

現在の進行状況バーの背景色 ( [COLORREF](/windows/win32/gdi/colorref)値として表されます)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor)メッセージを送信します。

##  <a name="getpos"></a>  CProgressCtrl::GetPos

プログレスバーの現在位置を取得します。

```
int GetPos();
```

### <a name="return-value"></a>戻り値

プログレスバーコントロールの位置。

### <a name="remarks"></a>Remarks

プログレスバーコントロールの位置は、画面上の物理的な位置ではなく、 [SetRange](#setrange)に示されている上限と下限の間にあります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>  CProgressCtrl::GetRange

プログレスバーコントロールの現在の下限、上限、または範囲を取得します。

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>パラメーター

*nLower*<br/>
プログレスバーコントロールの下限を受け取る整数への参照。

*nUpper*<br/>
プログレスバーコントロールの上限を受け取る整数への参照。

### <a name="remarks"></a>Remarks

この関数は、上限と上限の値をそれぞれ*Nlower*と*nlower*によって参照される整数にコピーします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>  CProgressCtrl::GetState

現在の進行状況バーコントロールの状態を取得します。

```
int GetState() const;
```

### <a name="return-value"></a>戻り値

現在の進行状況バーコントロールの状態。次の値のいずれかになります。

|[値]|状態|
|-----------|-----------|
|PBST_NORMAL|処理中|
|PBST_ERROR|Error|
|PBST_PAUSED|一時停止|

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PBM_GETSTATE](/windows/win32/Controls/pbm-getstate)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、進行状況バー コントロールにプログラムでアクセスするために使用される `m_progressCtrl` 変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>例

次のコード例では、現在の進行状況バーコントロールの状態を取得します。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>  CProgressCtrl::GetStep

現在の進行状況バーコントロールのプログレスバーの増分値を取得します。

```
int GetStep() const;
```

### <a name="return-value"></a>戻り値

プログレスバーのステップインクリメント。

### <a name="remarks"></a>Remarks

ステップインクリメントは、 [CProgressCtrl:: StepIt](#stepit)を呼び出すことによって進行状況バーの現在位置を増やす量です。

このメソッドは、Windows SDK で説明されている[PBM_GETSTEP](/windows/win32/Controls/pbm-getstep)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、進行状況バー コントロールにプログラムでアクセスするために使用される `m_progressCtrl` 変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>例

次のコード例では、現在の進行状況バーコントロールのステップインクリメントを取得します。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos

プログレスバーコントロールの現在位置を*nPos*で指定された増分に進め、新しい位置を反映するようにバーを再描画します。

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
位置を進める量。

### <a name="return-value"></a>戻り値

プログレスバーコントロールの前の位置。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor

現在の進行状況バーコントロールのプログレスインジケーターバーの色を設定します。

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*clrBar*|からプログレスインジケーターバーの新しい色を指定する[COLORREF](/windows/win32/gdi/colorref)値。 CLR_DEFAULT を指定すると、進行状況バーで既定の色が使用されます。|

### <a name="return-value"></a>戻り値

[COLORREF](/windows/win32/gdi/colorref)値として表示される進行状況インジケーターバーの前の色。進行状況インジケーターバーの色が既定の色の場合は CLR_DEFAULT。

### <a name="remarks"></a>Remarks

メソッド`SetBarColor`は、Windows Vista[テーマ](/windows/win32/Controls/visual-styles-overview)が有効でない場合にのみ、進行状況バーの色を設定します。

このメソッドは、Windows SDK で説明されている[PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、進行状況バー コントロールにプログラムでアクセスするために使用される `m_progressCtrl` 変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>例

次のコード例では、進行状況バーの色を赤、緑、青、または既定値に変更します。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor

プログレスバーの背景色を設定します。

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>パラメーター

*clrNew*<br/>
新しい背景色を指定する COLORREF 値。 CLR_DEFAULT 値を指定して、進行状況バーの既定の背景色を使用します。

### <a name="return-value"></a>戻り値

前の背景色を示す[COLORREF](/windows/win32/gdi/colorref)値。背景色が既定の色の場合は CLR_DEFAULT。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee

現在の進行状況バーコントロールに対してマーキーモードをオンまたはオフにします。

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*fMarqueeMode*|からマーキーモードをオンにする場合は TRUE、マーキーモードをオフにする場合は FALSE。|
|*N 期間*|からマーキーアニメーションの更新間の時間 (ミリ秒)。|

### <a name="return-value"></a>戻り値

このメソッドは常に TRUE を返します。

### <a name="remarks"></a>Remarks

[マーキーモード] をオンにすると、進行状況バーがアニメーション化され、シアターマーキーでのサインオンのようにスクロールします。

このメソッドは、Windows SDK で説明されている[PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、進行状況バー コントロールにプログラムでアクセスするために使用される `m_progressCtrl` 変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>例

次のコード例では、マーキースクロールアニメーションを開始および停止します。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>  CProgressCtrl::SetPos

*NPos*によって指定された進行状況バーコントロールの現在位置を設定し、新しい位置を反映するようにバーを再描画します。

```
int SetPos(int nPos);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
プログレスバーコントロールの新しい位置。

### <a name="return-value"></a>戻り値

プログレスバーコントロールの前の位置。

### <a name="remarks"></a>Remarks

プログレスバーコントロールの位置は、画面上の物理的な位置ではなく、 [SetRange](#setrange)に示されている上限と下限の間にあります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>  CProgressCtrl::SetRange

プログレスバーコントロールの範囲の上限と下限を設定し、新しい範囲を反映するようにバーを再描画します。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>パラメーター

*nLower*<br/>
範囲の下限を指定します (既定値は 0)。

*nUpper*<br/>
範囲の上限を指定します (既定値は 100)。

### <a name="remarks"></a>Remarks

このメンバー関数`SetRange32`は、プログレスコントロールの32ビット範囲を設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>  CProgressCtrl::SetState

現在の進行状況バー コントロールの状態を設定します。

```
int SetState(int iState);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iState*|からプログレスバーを設定する状態。 次のいずれかの値を使用します。<br /><br /> -PBST_NORMAL-進行中<br />-PBST_ERROR-エラー<br />-PBST_PAUSED-一時停止|

### <a name="return-value"></a>戻り値

現在の進行状況バー コントロールの直前の状態。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PBM_SETSTATE](/windows/win32/Controls/pbm-setstate)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、進行状況バー コントロールにプログラムでアクセスするために使用される `m_progressCtrl` 変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>例

次のコード例は、現在の進行状況バー コントロールの状態を一時停止または処理中に設定します。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>  CProgressCtrl::SetStep

プログレスバーコントロールのステップインクリメントを指定します。

```
int SetStep(int nStep);
```

### <a name="parameters"></a>パラメーター

*nStep*<br/>
新しいステップインクリメント。

### <a name="return-value"></a>戻り値

前のステップのインクリメント。

### <a name="remarks"></a>Remarks

ステップインクリメントは、の呼び出し`CProgressCtrl::StepIt`によって進行状況バーの現在位置を増やす量です。

既定のステップインクリメントは10です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>  CProgressCtrl::StepIt

プログレスバーコントロールの現在位置をステップごとに進め、新しい位置を反映するようにバーを再描画します。

```
int StepIt();
```

### <a name="return-value"></a>戻り値

プログレスバーコントロールの前の位置。

### <a name="remarks"></a>Remarks

ステップインクリメントは、 `CProgressCtrl::SetStep`メンバー関数によって設定されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
