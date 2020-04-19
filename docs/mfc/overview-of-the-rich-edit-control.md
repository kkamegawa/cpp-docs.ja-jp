---
title: リッチ エディット コントロールの概要
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: c45cb638ec860bb803c7de32065606dc3cc176b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160173"
---
# <a name="overview-of-the-rich-edit-control"></a>リッチ エディット コントロールの概要

> [!IMPORTANT]
>  ダイアログ ボックスで、リッチ エディット コントロールを使用しているかどうか (アプリケーションの SDI、MDI がかどうかに関係なくダイアログ ベースまたは)、呼び出す必要があります[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)したら前のダイアログに、ボックスが表示されます。 この関数を呼び出す標準的な場所は、プログラムの`InitInstance`メンバー関数。 ダイアログ ボックスで、最初の時刻のみを表示するたびに呼び出す必要はありません。 呼び出す必要はありません`AfxInitRichEdit`で作業している場合`CRichEditView`します。

リッチ エディット コントロール ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) テキストの書式設定のプログラミング インターフェイスを提供します。 ただし、アプリケーションでは、書式設定操作をユーザーに使用できるようにするために必要なすべてのユーザー インターフェイス コンポーネントを実装する必要があります。 つまり、豊富なは、選択したテキストの文字または段落の属性を変更するコントロールのサポートを編集します。 属性は、文字のいくつかの例では、太字、斜体、フォント ファミリ、し、サイズをポイントします。 段落の属性の例には、配置、余白、およびタブ ストップが含まれます。 まで、ユーザー インターフェイスを提供するツール バー ボタン、メニュー項目、または書式文字の ダイアログ ボックスであるかどうか。 リッチ エディット コントロールの現在の選択の属性を照会する関数もあります。 これらの関数をなど、属性の現在の設定を表示するのに使用して、太字の文字が属性の書式設定が選択されている場合は、コマンド UI のチェック マークを設定します。

文字および段落の書式設定の詳細については、次を参照してください。[文字書式](../mfc/character-formatting-in-rich-edit-controls.md)と[段落の書式設定](../mfc/paragraph-formatting-in-rich-edit-controls.md)このトピックで後述します。

豊富なは、ほぼすべての操作と複数行のエディット コントロールで使用される通知メッセージをコントロールのサポートに編集します。 したがって、既に編集コントロールを使用する変更できることに簡単に豊富なを使用するアプリケーションは、コントロールを編集します。 追加のメッセージと通知は、機能豊富なに固有の編集コントロールにアクセスするアプリケーションを有効にします。 エディット コントロールについては、次を参照してください。 [CEdit](../mfc/reference/cedit-class.md)します。

通知の詳細については、次を参照してください。[リッチ エディット コントロールからの通知](../mfc/notifications-from-a-rich-edit-control.md)このトピックで後述します。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
