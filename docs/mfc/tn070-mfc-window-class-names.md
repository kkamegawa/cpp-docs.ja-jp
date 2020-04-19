---
title: テクニカル ノート 70:MFC ウィンドウのクラス名
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 1d9b5de07bcc2545df6294557d1ac9f9d29e856c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513356"
---
# <a name="tn070-mfc-window-class-names"></a>テクニカル ノート 70:MFC ウィンドウのクラス名

> [!NOTE]
>  次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

MFC ウィンドウは、ウィンドウの機能を反映する動的に作成されたクラス名を使用します。 MFC は、アプリケーションによって生成されるフレームウィンドウ、ビュー、およびポップアップウィンドウに対して動的にクラス名を生成します。 MFC アプリケーションによって生成されるダイアログボックスとコントロールには、対象となるウィンドウのクラスに対して、Windows によって指定された名前が使用されます。

独自のウィンドウクラスを登録し、それを[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)のオーバーライドで使用することによって、動的に指定されたクラス名を置き換えることができます。 MFC に用意されているクラス名は、次の2つの形式のいずれかになります。

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

`%x`文字を置換する16進数字は、 [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)構造体のデータから入力されます。 MFC では、同じ**WNDCLASS**構造C++を必要とする複数のクラスが同じ登録済みウィンドウクラスを共有できるように、この手法を使用します。 ほとんどの単純な Win32 アプリケーションとは異なり、MFC アプリケーションには**WNDPROC**が1つしかないため、 **WNDCLASS**構造体を簡単に共有して時間とメモリを節約できます。 上に示した`%x`文字の置き換え可能な値は次のとおりです。

- **WNDCLASS hInstance**

- **WNDCLASS**

- **WNDCLASS**

- **WNDCLASS hbrBackground**

- **WNDCLASS**

最初の形式 (`Afx:%x:%x`) は、 **hcursor**、 **hbrBackground**、および**hIcon**がすべて**NULL**の場合に使用されます。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)<br/>
[テクニカル ノート 20: ID 名および番号に関する規約](../mfc/tn020-id-naming-and-numbering-conventions.md)
