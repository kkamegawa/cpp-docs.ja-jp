---
title: ビューを経由したユーザー入力の解釈
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: 3ef23ad74e1ff53d947453faa5682c5ecc1f4e43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310917"
---
# <a name="interpreting-user-input-through-a-view"></a>ビューを経由したユーザー入力の解釈

ビューの他のメンバー関数は、処理し、すべてのユーザー入力を解釈します。 通常、処理するため、ビュー クラスのメッセージ ハンドラー メンバー関数を定義します。

- Windows[メッセージ](../mfc/messages.md)マウスとキーボードの操作によって生成されました。

- [コマンド](../mfc/user-interface-objects-and-command-ids.md)からメニューのツールバーのボタン、およびアクセラレータ キー。

これらのメッセージ ハンドラー メンバー関数と、クリップボードからデータの移動などのデータ入力、選択した場合、または編集するには、次の操作を解釈します。

- マウスの動き、クリック、ドラッグとダブルクリック

- キー操作

- メニュー コマンド

Windows メッセージ ビューで処理は、アプリケーションのニーズによって異なります。

[メッセージの処理とマップ」](../mfc/message-handling-and-mapping.md)コマンドをメニュー項目とその他のユーザー インターフェイス オブジェクトを割り当てる方法と、コマンド ハンドラー関数をバインドする方法について説明します。 [メッセージの処理とマップ」](../mfc/message-handling-and-mapping.md)も MFC でのコマンドをルーティングする方法について説明し、それらのハンドラーが含まれているオブジェクトに標準の Windows メッセージを送信します。

たとえば、アプリケーションは、直接的なマウス、ビューの描画を実装する必要があります。 Scribble サンプルでは、開始、続行、および直線セグメントの描画を終了するそれぞれ WM_LBUTTONDOWN、WM_MOUSEMOVE、WM_LBUTTONUP メッセージを処理する方法を示します。 その一方で、選択内容のビューでのマウス クリックを解釈する必要がある場合があります。 ビューの`OnLButtonDown`ハンドラー関数をユーザーが描画または選択するかどうか確認します。 選択すると場合、ハンドラーをクリックし、ビュー内のオブジェクトの境界内かどうかを確認し、そうである場合は、選択されているオブジェクトを表示する表示を変更します。

ビューの編集 メニューの切り取り、コピー、貼り付け、またはクリップボードを使用して、選択したデータを削除するなど、特定のメニュー コマンドの処理もできます。 このようなハンドラーがクリップボードに関連するメンバーの一部の関数を呼び出すクラスの`CWnd`クリップボードとの間に、選択したデータ項目を転送します。

## <a name="see-also"></a>関連項目

[ビューの使い方](../mfc/using-views.md)
