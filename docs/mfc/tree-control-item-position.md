---
title: ツリー コントロールの項目位置
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
ms.openlocfilehash: 238cb40319d28a53592a594a72947f400720f935
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392480"
---
# <a name="tree-control-item-position"></a>ツリー コントロールの項目位置

ツリー コントロールに項目が追加されたときに、最初の項目の位置に設定されている ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) を使用して、`InsertItem`メンバー関数。 メンバー関数の呼び出しでは、親アイテムのハンドルと、その後、新しい項目が挿入される項目のハンドルを指定します。 2 番目のハンドルは、指定した親の子項目を識別する必要があります、またはこれらのいずれかの値: `TVI_FIRST`、 `TVI_LAST`、または`TVI_SORT`します。

ときに`TVI_FIRST`または`TVI_LAST`を指定すると、ツリー コントロールは、先頭または指定された親項目の子項目の一覧の末尾に新しい項目を配置します。 ときに`TVI_SORT`を指定すると、ツリー コントロール項目のラベルのテキストに基づいてアルファベット順に子項目のリストに新しい項目を挿入します。

アルファベット順に子項目の親項目の一覧を配置するには呼び出すことによって、 [SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren)メンバー関数。 この関数には、すべてのレベルの子項目の指定された親アイテムから降順がアルファベット順に並べ替えもかどうかを指定するパラメーターが含まれています。

[SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb)メンバー関数では、定義した条件に基づく子項目を並べ替えることができます。 この関数を呼び出すときに、ツリー コントロールが 2 つの子項目の相対順序を決定する必要があるときに呼び出すことができるアプリケーション定義のコールバック関数を指定します。 2 32 ビット アプリケーションで定義された値の比較対象となる項目と 3 番目の 32 ビット値を呼び出すときに指定するコールバック関数が受け取る`SortChildrenCB`します。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
