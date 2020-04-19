---
title: インライン アセンブリでの C++ 関数の呼び出し
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 666f7b2a59f0d48a14be54a439b6402f2a4d3128
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167271"
---
# <a name="calling-c-functions-in-inline-assembly"></a>インライン アセンブリでの C++ 関数の呼び出し

**Microsoft 固有の仕様**

`__asm`ブロックがないオーバー ロードされるグローバルの C++ 関数のみを呼び出すことができます。 オーバー ロードのグローバルな C++ 関数、または C++ メンバー関数を呼び出すと、コンパイラはエラーを発行します。

宣言された任意の関数を呼び出すこともできます**extern"C"** リンケージ。 これにより、 `__asm` 、C ライブラリ関数を呼び出すすべての標準ヘッダー ファイルがライブラリ関数を宣言するために、C++ プログラム内でブロック**extern"C"** リンケージ。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>