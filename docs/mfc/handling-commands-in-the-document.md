---
title: ドキュメントでのコマンドの処理
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: f3cce539d52bd04e97a6b5f84cbd833b05afb5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240575"
---
# <a name="handling-commands-in-the-document"></a>ドキュメントでのコマンドの処理

ドキュメント クラスには、メニュー項目、ツール バー ボタン、またはアクセラレータ キーによって生成される特定のコマンドも処理します。 既定では、`CDocument`保存を処理し、シリアル化を使用して [ファイル] メニュー コマンドの名前を付けて保存します。 その他のデータに影響を与えるコマンドは、ドキュメントのメンバー関数によっても処理があります。 たとえば、Scribble プログラムで、クラス`CScribDoc`編集のすべてのクリア コマンドは、ドキュメントに格納されているデータをすべて削除するハンドラーを提供します。 ドキュメントは、メッセージ マップを持つことができますが、ビューとは異なり、ドキュメントが標準の Windows メッセージを処理できません-のみ**WM_COMMAND**メッセージ、または「コマンド」。

## <a name="see-also"></a>関連項目

[ドキュメントの使い方](../mfc/using-documents.md)
