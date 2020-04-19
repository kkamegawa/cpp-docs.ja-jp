---
title: TN032:MFC 例外処理機構
ms.date: 11/04/2016
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 5b419fdcc4f20579b1a809dd8a5cf6a93f4fe835
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611417"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032:MFC 例外処理機構

Visual C の以前のバージョンが、標準の C++ 例外機構をサポートしていませんでしたし、MFC には、マクロが提供されている**TRY、CATCH、/THROW**代わりにで使用されました。 このバージョンの Visual C には、C++ の例外を完全にサポートしています。 この注は、前のマクロの高度な実装の詳細をいくつか紹介スタック ベースのオブジェクトを自動的にクリーンアップする方法についても触れます。 C++ の例外のスタック アンワインドを既定ではサポートされているためこの技術的な注意は必要はなくなりました。

参照してください[例外。MFC マクロと C++ 例外を使用して](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)MFC マクロと C++ のキーワードの違いの詳細についてはします。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
