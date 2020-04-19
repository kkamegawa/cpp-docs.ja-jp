---
title: クリップボード
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: 1db089110904ab88eb9c0c111d9da4e4e6869c82
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127908"
---
# <a name="clipboard"></a>クリップボード

この一連の記事では、MFC アプリケーションで Windows クリップボードのサポートを実装する方法について説明します。 Windows クリップボードは、次の2つの方法で使用されます。

- 切り取り、コピー、貼り付けなどの標準の編集メニューコマンドを実装する。

- OLE ドラッグアンドドロップによる一様なデータ転送の実装。

クリップボードは、変換元と変換先の間でデータを転送するための標準の Windows メソッドです。 また、OLE 操作では非常に便利です。 OLE の登場により、Windows には2つのクリップボードメカニズムがあります。 標準の Windows クリップボード API は引き続き使用できますが、OLE データ転送メカニズムによって補完されています。 OLE uniform data transfer (UDT) では、クリップボードとドラッグアンドドロップによる切り取り、コピー、貼り付けがサポートされています。

クリップボードは、Windows セッション全体で共有されるシステムサービスであるため、独自のハンドルやクラスを持ちません。 [CWnd](../mfc/reference/cwnd-class.md)クラスのメンバー関数を使用してクリップボードを管理します。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [各クリップボードメカニズムを使用する場合](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [従来の Windows クリップボード API の使用](../mfc/clipboard-using-the-windows-clipboard.md)

- [OLE クリップボード機構の使用](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [データのコピーと貼り付け](../mfc/clipboard-copying-and-pasting-data.md)

- [その他の形式の追加](../mfc/clipboard-adding-other-formats.md)

- [Windows クリップボード](/windows/win32/dataxchg/clipboard)

- [OLE ドラッグアンドドロップ](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>参照

[ユーザーインターフェイス要素](../mfc/user-interface-elements-mfc.md)
