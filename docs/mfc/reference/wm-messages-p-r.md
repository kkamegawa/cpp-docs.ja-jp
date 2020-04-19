---
title: Wm _ で始まるメッセージのハンドラー:P-R
ms.date: 11/04/2016
f1_keywords:
- ON_WM_RBUTTONUP
- ON_WM_PALETTECHANGED
- ON_WM_RBUTTONDBLCLK
- ON_WM_QUERYENDSESSION
- ON_WM_PARENTNOTIFY
- ON_WM_PALETTEISCHANGING
- ON_WM_QUERYOPEN
- ON_WM_PAINT
- ON_WM_QUERYNEWPALETTE
- ON_WM_RBUTTONDOWN
- ON_WM_RENDERALLFORMATS
- ON_WM_PAINTCLIPBOARD
- ON_WM_RENDERFORMAT
- ON_WM_QUERYDRAGICON
helpviewer_keywords:
- ON_WM_RENDERFORMAT [MFC]
- ON_WM_QUERYOPEN [MFC]
- ON_WM_RBUTTONDOWN [MFC]
- ON_WM_PAINTCLIPBOARD [MFC]
- ON_WM_QUERYNEWPALETTE [MFC]
- ON_WM_RBUTTONUP [MFC]
- ON_WM_PARENTNOTIFY [MFC]
- ON_WM_RBUTTONDBLCLK [MFC]
- ON_WM_PALETTECHANGED [MFC]
- ON_WM_PALETTEISCHANGING [MFC]
- ON_WM_QUERYDRAGICON [MFC]
- ON_WM_PAINT [MFC]
- ON_WM_RENDERALLFORMATS [MFC]
- ON_WM_QUERYENDSESSION [MFC]
- WM_ messages
ms.assetid: f46962e5-8329-4f1f-9b4d-fdad2a5ce1f8
ms.openlocfilehash: 283e7aa52008d76067249978d667ce641020a3bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309071"
---
# <a name="wm-messages-p---r"></a>Wm _ で始まるメッセージのハンドラー:P-R

次のマップ エントリは、関数プロトタイプに対応しています。

|マップ エントリ|関数プロトタイプ|
|---------------|------------------------|
|ON_WM_PAINT()|afx_msg void [OnPaint](../../mfc/reference/cwnd-class.md#onpaint)();|
|ON_WM_PAINTCLIPBOARD()|afx_msg void [OnPaintClipboard](../../mfc/reference/cwnd-class.md#onpaintclipboard)( CWnd*, HANDLE );|
|ON_WM_PALETTECHANGED()|afx_msg void [OnPaletteChanged](../../mfc/reference/cwnd-class.md#onpalettechanged)( CWnd* );|
|ON_WM_PALETTEISCHANGING()|afx_msg void [OnPaletteIsChanging](../../mfc/reference/cwnd-class.md#onpaletteischanging)( CWnd* );|
|ON_WM_PARENTNOTIFY()|afx_msg void [OnParentNotify](../../mfc/reference/cwnd-class.md#onparentnotify)( UINT, LONG );|
|ON_WM_POWERBROADCAST()|afx_msg UINT [OnPowerBroadcast](../../mfc/reference/cwnd-class.md#onpowerbroadcast)( UINT, UINT );|
|ON_WM_QUERYDRAGICON()|afx_msg HCURSOR [OnQueryDragIcon](../../mfc/reference/cwnd-class.md#onquerydragicon)()();|
|ON_WM_QUERYENDSESSION()|afx_msg BOOL [OnQueryEndSession](../../mfc/reference/cwnd-class.md#onqueryendsession)()();|
|ON_WM_QUERYNEWPALETTE()|afx_msg BOOL [OnQueryNewPalette](../../mfc/reference/cwnd-class.md#onquerynewpalette)()();|
|ON_WM_QUERYOPEN()|afx_msg BOOL [OnQueryOpen](../../mfc/reference/cwnd-class.md#onqueryopen)()();|
|ON_WM_RBUTTONDBLCLK()|afx_msg void [OnRButtonDblClk](../../mfc/reference/cwnd-class.md#onrbuttondblclk)( UINT, CPoint );|
|ON_WM_RBUTTONDOWN()|afx_msg void [OnRButtonDown](../../mfc/reference/cwnd-class.md#onrbuttondown)( UINT, CPoint );|
|ON_WM_RBUTTONUP()|afx_msg void [OnRButtonUp](../../mfc/reference/cwnd-class.md#onrbuttonup)( UINT, CPoint );|
|ON_WM_RENDERALLFORMATS()|afx_msg void [OnRenderAllFormats](../../mfc/reference/cwnd-class.md#onrenderallformats)();|
|ON_WM_RENDERFORMAT()|afx_msg void [OnRenderFormat](../../mfc/reference/cwnd-class.md#onrenderformat)( UINT );|

## <a name="see-also"></a>関連項目

[メッセージ マップ](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ で始まるメッセージのハンドラー](../../mfc/reference/handlers-for-wm-messages.md)
