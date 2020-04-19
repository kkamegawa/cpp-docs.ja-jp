---
title: ツリー コントロールのスタイル
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
ms.openlocfilehash: f5f28025d0349e9bcd95aba50d4110d304fed376
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510937"
---
# <a name="tree-control-styles"></a>ツリー コントロールのスタイル

ツリーコントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) スタイルは、ツリーコントロールの外観を制御します。 初期スタイルは、ツリーコントロールを作成するときに設定します。 **GWL_STYLE**を指定して、ツリーコントロールを作成した後にスタイルを取得および変更することができます、 [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) [Windows の関数](/windows/win32/api/winuser/nf-winuser-getwindowlongw)を指定して、 *nIndex*を指定するパラメーター。 スタイルの完全な一覧については、「Windows SDK の[ツリービューコントロールウィンドウスタイル](/windows/win32/Controls/tree-view-control-window-styles)」を参照してください。

**TVS_HASLINES**スタイルは、子項目を対応する親項目にリンクする線を描画することによって、ツリーコントロールの階層のグラフィック表示を拡張します。 このスタイルでは、階層のルートにある項目がリンクされません。 これを行うには、 **TVS_HASLINES**スタイルと**TVS_LINESATROOT**スタイルを組み合わせる必要があります。

ユーザーは、親アイテムをダブルクリックすることで、親アイテムの子アイテムのリストを展開または折りたたむことができます。 **TVS_SINGLEEXPAND**スタイルを持つツリーコントロールでは、項目が展開され、選択されていない項目が折りたたまれます。 マウスを使用して選択した項目をシングルクリックすると、その項目が閉じられます。 選択した項目が開いたときにシングルクリックされた場合は、折りたたまれます。

**TVS_HASBUTTONS**スタイルを持つツリーコントロールは、各親項目の左側にボタンを追加します。 このボタンをクリックすると、親項目をダブルクリックする代わりに、子項目を展開したり折りたたんだりすることができます。 **TVS_HASBUTTONS**は、階層のルートにある項目にボタンを追加しません。 これを行うには、 **TVS_HASLINES**、 **TVS_LINESATROOT**、および**TVS_HASBUTTONS**を組み合わせる必要があります。

**TVS_EDITLABELS**スタイルを使用すると、ユーザーがツリーコントロール項目のラベルを編集できるようになります。 ラベルの編集の詳細については、このトピックで後述する「[ツリーコントロールラベルの編集](../mfc/tree-control-label-editing.md)」を参照してください。

**TVS_NOTOOLTIPS**スタイルは、ツリービューコントロールの自動ツールヒント機能を無効にします。 この機能により、タイトル全体が現在表示されていない場合、マウスカーソルの下にある項目のタイトルを含むツールヒントが自動的に表示されます。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
