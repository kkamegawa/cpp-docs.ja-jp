---
title: プロパティ シートへのコントロールの追加
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 07b384b2db36ae59d4de8b99d9c07396ce793979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394794"
---
# <a name="adding-controls-to-a-property-sheet"></a>プロパティ シートへのコントロールの追加

既定では、プロパティ シートは、プロパティ ページ、タブ インデックス、および OK、Cancel、および適用ボタン ウィンドウ領域を割り当てます。 (モードレス プロパティ シートが [ok] を取り消して、ボタンに適用されます。)他のコントロールは、プロパティ シートを追加することができます。 たとえば、現在の設定がどの外部オブジェクトに適用した場合、ユーザーを表示するプロパティ ページの領域の右側にプレビュー ウィンドウを追加できます。

プロパティ シートのダイアログ ボックスにコントロールを追加することができます、`OnCreate`ハンドラー。 通常、その他のコントロールに対応するには、プロパティ シートのダイアログ ボックスのサイズを拡張する必要があります。 基本クラスを呼び出した後**CPropertySheet::OnCreate**、呼び出す[GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect)現在割り当てられているプロパティ シート ウィンドウの高さと幅を取得するには、展開、四角形のディメンション、および呼び出し[MoveWindow](../mfc/reference/cwnd-class.md#movewindow)プロパティ シート ウィンドウのサイズを変更します。

## <a name="see-also"></a>関連項目

[プロパティ シート](../mfc/property-sheets-mfc.md)<br/>
[CPropertyPage クラス](../mfc/reference/cpropertypage-class.md)<br/>
[CPropertySheet クラス](../mfc/reference/cpropertysheet-class.md)
