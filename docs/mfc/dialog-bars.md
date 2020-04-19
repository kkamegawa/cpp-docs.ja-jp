---
title: ダイアログ バー
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: e4e843327daba6f0aa468cb07394165bc70fa7f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389638"
---
# <a name="dialog-bars"></a>ダイアログ バー

ダイアログ バーは、ツールバー、一種の[コントロール バー](../mfc/control-bars.md)あらゆる種類のコントロールを含めることができます。 モードレス ダイアログ ボックスでは、特性があるため、 [CDialogBar](../mfc/reference/cdialogbar-class.md)オブジェクトはより強力なツールバーを提供します。

ツールバーのいくつかの主な違いがあると`CDialogBar`オブジェクト。 A `CDialogBar` Visual C ダイアログ エディターを使用して作成およびあらゆる種類の Windows コントロールを含めることができる、ダイアログ テンプレート リソースからオブジェクトを作成します。 ユーザーはコントロールからコントロールのタブにします。 親フレーム ウィンドウの任意の部分を持つダイアログ バーを配置するか、親のサイズが変更された場合の場所に残すにも、配置スタイルを指定できます。 次の図には、さまざまなコントロールをダイアログ バーが表示されます。

![VC ダイアログ バー](../mfc/media/vc378t1.gif "VC ダイアログ バー") <br/>
ダイアログ バー

その他の点では、使用、`CDialogBar`オブジェクトはモードレス ダイアログ ボックスでの作業に似ています。 設計およびダイアログ リソースを作成するには、ダイアログ エディターを使用します。

ダイアログ バーの長所の 1 つはボタン以外のコントロールを含めることができます。

独自のダイアログ クラスを派生させるのには通常は`CDialog`、ダイアログ バーの独自のクラスを通常は派生されません。 ダイアログ バーのメイン ウィンドウとダイアログ バー コントロールの通知メッセージ、拡張機能として**BN_CLICKED**または**EN_CHANGE**、横棒グラフ、メイン ウィンドウ、ダイアログ ボックスの親に送信されます。

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス要素](../mfc/user-interface-elements-mfc.md)<br/>
[サンプル](../overview/visual-cpp-samples.md)
