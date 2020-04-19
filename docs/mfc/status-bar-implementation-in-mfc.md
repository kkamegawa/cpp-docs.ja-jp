---
title: MFC でのステータス バーの実装
ms.date: 11/19/2018
f1_keywords:
- COldStatusBar
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
ms.openlocfilehash: abd16ecb5e6a492bc42c747f60ec0859e1bc05cb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346414"
---
# <a name="status-bar-implementation-in-mfc"></a>MFC でのステータス バーの実装

A [CStatusBar](../mfc/reference/cstatusbar-class.md)オブジェクトはテキスト出力ペインの行を持つコントロール バーです。 メッセージの行と状態インジケーターとして、出力ウィンドウがよく使用されます。 例には、選択されたメニュー コマンドを簡単に説明するメニュー ヘルプ メッセージ行と SCROLL LOCK、NUM LOCK、およびその他のキーの状態を示すインジケーターが含まれます。

クラスを使用して MFC バージョン 4.0 の時点でステータス バーが実装されます[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)、ステータス バー コモン コントロールをカプセル化します。 旧バージョンと互換性のため、MFC では古いステータス バーの実装クラスで`COldStatusBar`します。 以前のバージョンの MFC のドキュメントに記載`COldStatusBar``CStatusBar`します。

[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)、メンバー関数は、新しい MFC 4.0 では、することができますステータス バーのカスタマイズなどの追加機能の Windows コモン コントロールのサポートを活用します。 `CStatusBar` メンバー関数は、ほとんどの Windows コモン コントロール以外の機能を提供します。ただし、呼び出す`GetStatusBarCtrl`、さらに多くのステータス バーの特性、ステータス バーを付けることができます。 呼び出すと`GetStatusBarCtrl`への参照が返されます、`CStatusBarCtrl`オブジェクト。 その参照を使用するには、ステータス バー コントロールを操作します。

次の図には、いくつかのインジケーターを表示するステータス バーが表示されます。

![ステータス バー](../mfc/media/vc37dy1.gif "ステータス バー") <br/>
ステータス バー

ツールバーのようにステータス バーのオブジェクトは親フレーム ウィンドウに埋め込まれているし、フレーム ウィンドウが作成されるときに自動的に構築します。 すべてのコントロール バーのように、ステータス バーは自動的に破棄も親フレームが破棄されるときにします。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ステータス バー ペインのテキストの更新](../mfc/updating-the-text-of-a-status-bar-pane.md)

- MFC クラス[CStatusBar](../mfc/reference/cstatusbar-class.md)と[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [コントロール バー](../mfc/control-bars.md)

- [ダイアログ バー](../mfc/dialog-bars.md)

- [ツールバー (MFC ツールバーの実装)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>関連項目

[ステータス バー](../mfc/status-bars.md)
