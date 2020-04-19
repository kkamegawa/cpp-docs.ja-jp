---
title: naked 関数呼び出し
ms.date: 11/04/2016
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
ms.openlocfilehash: 242fe83807c6608a09492d0f1f817e3b6e50e530
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857399"
---
# <a name="naked-function-calls"></a>naked 関数呼び出し

**Microsoft 固有の仕様**

**生**の属性を使用して宣言された関数は、プロローグまたはエピローグコードなしで生成されるため、[インラインアセンブラー](../assembler/inline/inline-assembler.md)を使用して独自のカスタムプロローグ/エピローグシーケンスを記述できます。 naked 関数は高度な機能です。 これにより、C/C++ 以外のコンテキストから呼び出される関数を宣言して、パラメーターの存在する場所や保持されるレジスタについて、異なる想定をすることができます。 例としては、割り込みハンドラーのようなルーチンが挙げられます。 この機能は、仮想デバイス ドライバー (VxD) を作成するときに特に便利です。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [naked](../cpp/naked-cpp.md)

- [naked 関数に関する規則と制限](../cpp/rules-and-limitations-for-naked-functions.md)

- [プロローグ/エピローグ コードの記述に関する考慮事項](../cpp/considerations-for-writing-prolog-epilog-code.md)

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[呼び出し規約](../cpp/calling-conventions.md)