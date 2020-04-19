---
title: プログレス コントロールのスタイル
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: 3adbd32456b1375bd2dc8574220e083ca3d83ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306815"
---
# <a name="styles-for-the-progress-control"></a>プログレス コントロールのスタイル

プログレス コントロールを最初に作成するときに ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create))、使用、 *dwStyle*プログレス コントロールの目的のウィンドウ スタイルを指定するパラメーター。 次の一覧では、該当するウィンドウ スタイルについて説明します。 コントロールには、ここに挙げた以外の任意のウィンドウ スタイルは無視されます。 常に、ダイアログ ボックスの親の通常の子ウィンドウとしてコントロールを作成する必要があります。

|ウィンドウ スタイル|効果|
|------------------|------------|
|WS_BORDER|ウィンドウの周囲に罫線を作成します。|
|WS_CHILD|子ウィンドウを作成します (に常に使用する必要があります`CProgressCtrl`)。|
|WS_CLIPCHILDREN|親ウィンドウ内に描画するときに、子ウィンドウにより占有されている領域を除外します。 親ウィンドウを作成するときに使用します。|
|WS_CLIPSIBLINGS|相対的な子ウィンドウをクリップします。|
|WS_DISABLED|最初に無効になっているウィンドウを作成します。|
|WS_VISIBLE|最初に表示されているウィンドウを作成します。|
|WS_TABSTOP|ユーザーをそこに移動して、TAB キーを押したときに、コントロールがフォーカスを受け取ることができますを指定します。|

さらに、2 つのスタイル、進行状況コントロールのみに適用される PBS_VERTICAL と PBS_SMOOTH を指定できます。

PBS_VERTICAL を使用して、コントロールを水平方向にではなく縦方向に回転します。 PBS_SMOOTH を使用すると、コントロールに段階的入力小さな区別された四角形を表示するのではなく、コントロールを完全に入力します。

PBS_SMOOTH 形式: なし

![標準の進行状況バー スタイル](../mfc/media/vc4ruw1.gif "標準の進行状況バー スタイル")

PBS_SMOOTH と PBS_VERTICAL スタイル。

![進行状況バーがスタイル、スムーズおよび垂直方向](../mfc/media/vc4ruw2.gif "バーのスタイル、スムーズおよび垂直方向の進行状況")

詳細については、次を参照してください。[ウィンドウ スタイル](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc)で、 *MFC リファレンス*します。

## <a name="see-also"></a>関連項目

[CProgressCtrl の使い方](../mfc/using-cprogressctrl.md)
