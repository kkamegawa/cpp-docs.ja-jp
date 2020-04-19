---
title: CClientDC クラス
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: 46428740d052c70218d4443395777428cdf3c3b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507336"
---
# <a name="cclientdc-class"></a>CClientDC クラス

は、構築時に Windows functions [GetDC](/windows/win32/api/winuser/nf-winuser-getdc)を呼び出し、破棄時に[ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc)を行います。

## <a name="syntax"></a>構文

```
class CClientDC : public CDC
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CClientDC:: CClientDC](#cclientdc)|に接続`CClientDC`されたオブジェクトを構築します。`CWnd`|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CClientDC:: m_hWnd](#m_hwnd)|この`CClientDC`が有効なウィンドウの HWND。|

## <a name="remarks"></a>Remarks

これは、 `CClientDC`オブジェクトに関連付けられているデバイスコンテキストがウィンドウのクライアント領域であることを意味します。

の`CClientDC`詳細については、「[デバイスコンテキスト](../../mfc/device-contexts.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cclientdc"></a>CClientDC:: CClientDC

PWnd が`CClientDC`指す[CWnd](../../mfc/reference/cwnd-class.md)のクライアント領域にアクセスするオブジェクトを構築します。

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
デバイスコンテキストオブジェクトがアクセスするクライアント領域があるウィンドウ。

### <a name="remarks"></a>Remarks

コンストラクターは、Windows 関数[GetDC](/windows/win32/api/winuser/nf-winuser-getdc)を呼び出します。

`CResourceException` Windows`GetDC`の呼び出しが失敗した場合、例外 (型) がスローされます。 Windows によって使用可能なデバイスコンテキストがすべて既に割り当てられている場合、デバイスコンテキストを使用できない可能性があります。 アプリケーションは、Windows で任意の時点で使用可能な5つの共通表示コンテキストを競合しています。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CClientDC:: m_hWnd

オブジェクトを構築`CWnd`するために使用する`HWND` `CClientDC`ポインターの。

```
HWND m_hWnd;
```

### <a name="remarks"></a>Remarks

*m_hWnd*は保護された変数です。

### <a name="example"></a>例

  [Cclientdc:: cclientdc](#cclientdc)の例を参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプル MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC クラス](../../mfc/reference/cdc-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDC クラス](../../mfc/reference/cdc-class.md)
