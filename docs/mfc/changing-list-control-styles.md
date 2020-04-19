---
title: リスト コントロール スタイルの変更
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: b3cc65ce6ef0e84eaa2f6738cb18b6b862a6473a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509053"
---
# <a name="changing-list-control-styles"></a>リスト コントロール スタイルの変更

リストコントロール ([CListCtrl](../mfc/reference/clistctrl-class.md)) のウィンドウスタイルは、作成後いつでも変更できます。 ウィンドウのスタイルを変更することで、コントロールが使用するビューの種類を変更できます。 たとえば、エクスプローラーをエミュレートするために、コントロールを異なるビュー (アイコンビュー、リストビューなど) に切り替えるためのメニュー項目またはツールバーボタンを指定できます。

たとえば、ユーザーがメニュー項目を選択したときに、 [Getwindowlong](/windows/win32/api/winuser/nf-winuser-getwindowlongw)を呼び出して、コントロールの現在のスタイルを取得し、 [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw)を呼び出してスタイルをリセットすることができます。 詳細については、「Windows SDK での[リストビューコントロールの使用](/windows/win32/Controls/using-list-view-controls)」を参照してください。

使用可能なスタイルは、[作成](../mfc/reference/clistctrl-class.md#create)中に一覧表示されます。 **になっ**、 **LVS_SMALLICON**、 **LVS_LIST**、および**LVS_REPORT**の各スタイルは、4つのリストコントロールビューを指定します。

## <a name="extended-styles"></a>拡張スタイル

リストコントロールの標準スタイルに加えて、拡張スタイルと呼ばれる別のセットもあります。 Windows SDK の[拡張リストビュースタイル](/windows/win32/Controls/extended-list-view-styles)で説明したこれらのスタイルには、リストコントロールの動作をカスタマイズするための便利な機能がいくつか用意されています。 特定のスタイル (ホバー選択など) の動作を実装するには、必要なスタイルを渡して、 [CListCtrl:: SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle)を呼び出します。 関数呼び出しの例を次に示します。

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  ホバー選択を機能させるには、 **LVS_EX_ONECLICKACTIVATE**または**LVS_EX_TWOCLICKACTIVATE**をオンにする必要もあります。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
