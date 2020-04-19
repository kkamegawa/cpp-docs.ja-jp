---
title: CStatusBarCtrl の設定値
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: b41997fb9342a651260bc2196d212016dc0deb7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307693"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl の設定値

既定の位置を[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)ステータス ウィンドウが、親ウィンドウの下部には、親ウィンドウのクライアント領域の上部に表示されるようにする CCS_TOP スタイルを指定することができます。

右端にあるサイズ変更グリップを含める SBARS_SIZEGRIP スタイルを指定することができます、`CStatusBarCtrl`ステータス ウィンドウ。 サイズ変更グリップはサイズ変更境界線; に似ていますユーザーがクリックして親ウィンドウのサイズをドラッグ四角形の領域になります。

> [!NOTE]
>  CCS_TOP と SBARS_SIZEGRIP スタイルを結合する場合、結果のサイズ変更グリップは場合でも、システムは、ステータス ウィンドウに描画と機能しません。

ステータス ウィンドウのウィンドウ プロシージャは、初期サイズおよびコントロール ウィンドウの位置に自動的に設定します。 幅は、親ウィンドウのクライアント領域の場合と同じです。 高さは、ステータス ウィンドウのデバイス コンテキストに現在選択されているフォントのメトリックでは、ウィンドウの境界線の幅に基づきます。

WM_SIZE メッセージを受信するたびに、ウィンドウ プロシージャは、ステータス ウィンドウのサイズを自動調整します。 通常、親ウィンドウのサイズが変更されたときに、親は、ステータス ウィンドウに WM_SIZE メッセージを送信します。

ステータス ウィンドウの描画領域の高さの最小値を設定するには呼び出すことによって[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)、最小の高さをピクセル単位で指定します。 描画領域では、ウィンドウの境界線は含まれません。

呼び出すことによってステータス ウィンドウの境界線の幅を取得する[GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)します。 このメンバー関数には、水平方向の境界線、垂直方向の境界線の四角形の間の境界線の幅を受信する 3 要素の配列へのポインターが含まれています。

## <a name="see-also"></a>関連項目

[CStatusBarCtrl の使い方](../mfc/using-cstatusbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
