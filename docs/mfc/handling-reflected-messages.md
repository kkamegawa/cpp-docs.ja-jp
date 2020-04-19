---
title: 反映されたメッセージの処理方法
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 973e8cff24eca37b1806207d081636f0d1b38365
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240562"
---
# <a name="handling-reflected-messages"></a>反映されたメッセージの処理方法

メッセージがリフレクションでは、コントロールのメッセージを処理できます。 **WM_CTLCOLOR**、 **WM_COMMAND**、および**WM_NOTIFY**、コントロール自体の内部。 これによってより自己完結型で移植可能なコントロール。 メカニズムは、(旧称 OLE コントロール) の ActiveX コントロールおよび Windows のコモン コントロールとは動作します。

メッセージがリフレクションを使用して、再利用できる、 `CWnd`-派生クラスをより簡単にします。 リフレクションの動作を使用してメッセージ[CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)、特別なを使用して**ON_XXX_REFLECT**メッセージ マップ エントリ: たとえば、 **ON_CTLCOLOR_REFLECT**と**ON_CONTROL_REFLECT**します。 [テクニカル ノート 62](../mfc/tn062-message-reflection-for-windows-controls.md)メッセージ リフレクションについて詳しく説明します。

## <a name="what-do-you-want-to-do"></a>どうしたいんですか

- [メッセージ リフレクションについての詳細します。](../mfc/tn062-message-reflection-for-windows-controls.md)

- [コモン コントロールのメッセージ リフレクションを実装します。](../mfc/tn062-message-reflection-for-windows-controls.md)

- [ActiveX コントロールのメッセージ リフレクションを実装します。](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>関連項目

[メッセージ ハンドラー関数の宣言](../mfc/declaring-message-handler-functions.md)
