---
title: __asm ブロックでの C または C++ シンボルの使用
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: fc22af8ec04d616eb8f5566b118e19c405605401
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166543"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>__asm ブロックでの C または C++ シンボルの使用

**Microsoft 固有の仕様**

`__asm`ブロックは、ブロックが表示されているスコープ内の任意の C または C++ シンボルを参照してください。 (C および C++ のシンボルは、変数名、関数名、およびラベルは、シンボリック定数ではない名前または`enum`メンバー。 呼び出すことはできません C++ メンバー関数。)

C および C++ の記号を使用するいくつかの制限が適用されます。

- 各アセンブリ言語のステートメントは、1 つの C または C++ シンボルのみに含めることができます。 複数のシンボル命令で使用できる、同じアセンブリでのみ**LENGTH**、**TYPE**、および**SIZE**式。

- 参照される関数、`__asm`ブロックは、前のプログラム (プロトタイプ) 宣言する必要があります。 それ以外の場合、コンパイラと区別できない関数名のラベル、`__asm`ブロックします。

- `__asm`ブロックと同じスペル (大文字小文字) 予約 MASM 単語として、C または C++ シンボルを使用することはできません。 MASM の予約語は命令の名前など**PUSH**と SI などの名前を登録します。

- 構造体と共用体タグで認識されない`__asm`ブロックします。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでの C または C++ の使用](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
