---
title: CPaintDC クラス
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503138"
---
# <a name="cpaintdc-class"></a>CPaintDC クラス

[CDC](../../mfc/reference/cdc-class.md)から派生したデバイスコンテキストクラス。

## <a name="syntax"></a>構文

```
class CPaintDC : public CDC
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPaintDC:: CPaintDC](#cpaintdc)|指定し`CPaintDC`た[CWnd](../../mfc/reference/cwnd-class.md)に接続されているを構築します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CPaintDC:: m_ps](#m_ps)|クライアント領域の描画に使用される[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)を格納します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CPaintDC:: m_hWnd](#m_hwnd)|この`CPaintDC`オブジェクトがアタッチされている HWND。|

## <a name="remarks"></a>Remarks

このメソッドは、構築時に[cwnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint)を実行し、破棄時に[Cwnd:: endpaint](../../mfc/reference/cwnd-class.md#endpaint)を実行します。

オブジェクト`CPaintDC`は、 [WM_PAINT](/windows/win32/gdi/wm-paint)メッセージに応答する場合にのみ使用できます。通常`OnPaint`は、メッセージハンドラーのメンバー関数で使用します。

の使用方法`CPaintDC`の詳細については、「[デバイスコンテキスト](../../mfc/device-contexts.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cpaintdc"></a>CPaintDC:: CPaintDC

オブジェクトを`CPaintDC`構築し、アプリケーションウィンドウに描画を準備し、 [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)構造体を[m_ps](#m_ps)メンバー変数に格納します。

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
オブジェクトが`CWnd` `CPaintDC`属するオブジェクトを指します。

### <a name="remarks"></a>Remarks

Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) の呼び出しが`CResourceException`失敗した場合、例外 (型) がスローされます。 Windows によって使用可能なデバイスコンテキストがすべて既に割り当てられている場合、デバイスコンテキストを使用できない可能性があります。 アプリケーションは、Windows で任意の時点で使用可能な5つの共通表示コンテキストを競合しています。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CPaintDC:: m_hWnd

`HWND` この`CPaintDC`オブジェクトがアタッチされる。

```
HWND m_hWnd;
```

### <a name="remarks"></a>Remarks

*m_hWnd*は、hWnd 型の保護された変数です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>CPaintDC:: m_ps

`m_ps`は、 [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)型のパブリックメンバー変数です。

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Remarks

これは、 `PAINTSTRUCT` [CWnd:: beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)によって渡され、入力されるです。

に`PAINTSTRUCT`は、 `CPaintDC`オブジェクトに関連付けられたウィンドウのクライアント領域を描画するためにアプリケーションが使用する情報が含まれています。

デバイスコンテキストハンドルには、 `PAINTSTRUCT`を介してアクセスできることに注意してください。 ただし、CDC から継承した`m_hDC` `CPaintDC`メンバー変数を介して、ハンドルに直接アクセスできます。

### <a name="example"></a>例

  [CPaintDC:: m_hWnd](#m_hwnd)の例を参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプル MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC クラス](../../mfc/reference/cdc-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
