---
title: CWindowDC クラス
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 0ef9b4917dc834eb8335690f9b0d171245f5c170
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502154"
---
# <a name="cwindowdc-class"></a>CWindowDC クラス

`CDC`の派生クラスです。

## <a name="syntax"></a>構文

```
class CWindowDC : public CDC
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|`CWindowDC` オブジェクトを構築します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|この`CWindowDC`がアタッチされている HWND。|

## <a name="remarks"></a>Remarks

構築時に Windows 関数[GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)を呼び出し、破棄時に[ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc)します。 これは、オブジェクト`CWindowDC`が[CWnd](../../mfc/reference/cwnd-class.md)の画面領域全体 (クライアント領域と非クライアント領域の両方) にアクセスすることを意味します。

の使用方法`CWindowDC`の詳細については、「[デバイスコンテキスト](../../mfc/device-contexts.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>必要条件

ヘッダー: afxwin.h

##  <a name="cwindowdc"></a>CWindowDC::CWindowDC

*PWnd*が`CWindowDC`指す`CWnd`オブジェクトの画面領域全体 (クライアントと非クライアントの両方) にアクセスするオブジェクトを構築します。

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
デバイスコンテキストオブジェクトがアクセスするクライアント領域があるウィンドウ。

### <a name="remarks"></a>Remarks

コンストラクターは、Windows 関数[GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)を呼び出します。

`CResourceException` Windows`GetWindowDC`の呼び出しが失敗した場合、例外 (型) がスローされます。 Windows によって使用可能なデバイスコンテキストがすべて既に割り当てられている場合、デバイスコンテキストを使用できない可能性があります。 アプリケーションは、Windows で任意の時点で使用可能な5つの共通表示コンテキストを競合しています。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CWindowDC:: m_hWnd

`CWnd`ポインターの HWND は、 `CWindowDC`オブジェクトを構築するために使用されます。

```
HWND m_hWnd;
```

### <a name="remarks"></a>Remarks

`m_hWnd`は、HWND 型の保護された変数です。

### <a name="example"></a>例

  [CWindowDC:: CWindowDC](#cwindowdc)の例を参照してください。

## <a name="see-also"></a>関連項目

[CDC クラス](../../mfc/reference/cdc-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDC クラス](../../mfc/reference/cdc-class.md)
