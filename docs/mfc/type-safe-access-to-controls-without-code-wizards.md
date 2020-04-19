---
title: コード ウィザードを使用しない、コントロールへのタイプ セーフ アクセス
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 5b4b604bf42a327edf3ac7a83dcfc42a5e0d8c54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180812"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>コード ウィザードを使用しない、コントロールへのタイプ セーフ アクセス

タイプ セーフ アクセス コントロールを作成する最初のアプローチは、クラスの戻り値の型をキャストするインライン メンバー関数を使用して`CWnd`の`GetDlgItem`この例のように、適切な C++ コントロール型にメンバー関数。

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

このメンバー関数は、コードを次のようなタイプ セーフな方法でコントロールにアクセスし使用できます。

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロールへのタイプ セーフ アクセス](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[コード ウィザードを使用した、コントロールへのタイプ セーフ アクセス](../mfc/type-safe-access-to-controls-with-code-wizards.md)
