---
title: クリップボード:OLE クリップボード機構の使用
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: 0f2c10f4a88b723d1ab9f4bb0ca903987359c9fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508909"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>クリップボード:OLE クリップボード機構の使用

OLE では、クリップボードを使用してデータを転送するために、標準形式といくつかの OLE 固有の形式が使用されます。

アプリケーションからデータを切り取ったりコピーしたりすると、データはクリップボードに保存され、後で貼り付け操作で使用できるようになります。 このデータは、さまざまな形式になっています。 ユーザーがクリップボードからデータを貼り付けることを選択した場合、アプリケーションでは、使用する形式を選択できます。 アプリケーションは、ユーザーが特に特定の形式を指定しない限り、[特殊な貼り付け] を使用して、最も多くの情報を提供する形式を選択するように記述する必要があります。 続行する前に、「[データオブジェクトとデータソース (OLE)](../mfc/data-objects-and-data-sources-ole.md) 」のトピックを読むことをお勧めします。 これらの例では、データ転送のしくみと、それらをアプリケーションに実装する方法の基本について説明します。

Windows では、クリップボードを介してデータを転送するために使用できる標準形式がいくつか定義されています。 これには、メタファイル、テキスト、ビットマップなどが含まれます。 OLE では、多くの OLE 固有の書式も定義されています。 これらの標準形式よりも詳細な情報が必要なアプリケーションの場合は、独自のカスタムクリップボード形式を登録することをお勧めします。 これを行うには、Win32 API 関数[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)を使用します。

たとえば、Microsoft Excel では、スプレッドシートのカスタム書式が登録します。 この形式には、ビットマップなど、より多くの情報が含まれています。 スプレッドシート形式をサポートするアプリケーションにこのデータが貼り付けられると、スプレッドシートのすべての数式と値が保持され、必要に応じて更新できます。 Microsoft Excel では、OLE アイテムとして貼り付けることができるように、データを形式でクリップボードに配置することもできます。 OLE ドキュメントコンテナーでは、この情報を埋め込みアイテムとして貼り付けることができます。 この埋め込み項目は、Microsoft Excel を使用して変更できます。 クリップボードには、スプレッドシート上で選択された範囲のイメージの単純なビットマップも含まれています。 これは、OLE ドキュメントコンテナーまたはペイントなどのビットマップエディターに貼り付けることもできます。 ただし、ビットマップの場合は、データをスプレッドシートとして操作する方法はありません。

クリップボードから最大量の情報を取得するには、クリップボードからデータを貼り付ける前に、アプリケーションでこれらのカスタム形式を確認する必要があります。

たとえば、Cut コマンドを有効にするには、次のようなハンドラーを記述します。

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [データのコピーと貼り付け](../mfc/clipboard-copying-and-pasting-data.md)

- [その他の形式の追加](../mfc/clipboard-adding-other-formats.md)

- [Windows クリップボードの使用](../mfc/clipboard-using-the-windows-clipboard.md)

- [OLE](../mfc/ole-background.md)

- [OLE データオブジェクトとデータソース、および uniform data transfer](../mfc/data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>関連項目

[クリップボード](../mfc/clipboard.md)
