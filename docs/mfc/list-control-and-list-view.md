---
title: リスト コントロールとリスト ビュー
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: 5c9612a22eab27d568c0dbb86d29ba031fe5985e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365333"
---
# <a name="list-control-and-list-view"></a>リスト コントロールとリスト ビュー

便宜上、MFC では、2 つの方法でリスト コントロールがカプセル化します。 リスト コントロールを使用することができます。

- 埋め込むことによって、直接、 [CListCtrl](../mfc/reference/clistctrl-class.md)ダイアログ クラス内のオブジェクト。

- クラスを使用して、直接[CListView](../mfc/reference/clistview-class.md)します。

`CListView` 簡単にコントロールをカプセル化 MFC ドキュメント/ビュー アーキテクチャは、リスト コントロールの統合と同じ[CEditView](../mfc/reference/ceditview-class.md)エディット コントロールをカプセル化: コントロールが MFC ビューの領域全体を入力します。 (ビュー*は*にキャスト、コントロール`CListView`)。

A`CListView`オブジェクトから継承[CCtrlView](../mfc/reference/cctrlview-class.md)し、その基本クラスし、基になるリスト コントロールを取得するメンバー関数を追加します。 メンバーの表示を使用して、ビューとして使用します。 使用して、 [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)リスト コントロールのメンバー関数へのアクセスを取得します。 これらのメンバーを使用します。

- 追加、削除、またはリスト内の「アイテム」を操作します。

- 設定またはコントロール属性の一覧を取得します。

参照を取得する、`CListCtrl`基になる、 `CListView`、呼び出す`GetListCtrl`一覧ビュー クラスから。

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

このトピックでは、リスト コントロールを使用する両方の方法について説明します。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
