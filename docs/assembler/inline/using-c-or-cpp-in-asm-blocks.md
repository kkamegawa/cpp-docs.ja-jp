---
title: __asm ブロックでの C または C++ の使用
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
ms.openlocfilehash: 16b298b92a4ba40d9091499a1821ad4f3c413d6c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854525"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>__asm ブロックでの C または C++ の使用

**Microsoft 固有の仕様**

インラインアセンブリ命令は C またはC++ステートメントと混在させることができるため、c C++または変数を名前で参照し、これらの言語の他の多くの要素を使用することができます。

`__asm` ブロックは、次の言語要素を使用できます。

- ラベル、変数名、関数名を含むシンボル

- シンボル定数と `enum` メンバーを含む定数

- マクロおよびプリプロセッサディレクティブ

- コメント ( __/\* \*/__ と __//__ )

- 型名 (MASM の型が有効である任意の場所)

- `typedef` などの演算子で使用される一般に、名**PTR**と**TYPE**または構造体または共用体のメンバーを指定するには

`__asm` ブロック内では、C 表記またはアセンブラー基数表記 (0x100 と100h は同等) で整数定数を指定できます。 これにより、C で定数を定義 (`#define`) して、C またはC++プログラムのアセンブリ部分の両方で使用できます。 また、定数を8進数で指定するには、その前に0を指定します。 たとえば、0777は8進数の定数を指定します。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [__asm ブロックでの演算子の使用](../../assembler/inline/using-operators-in-asm-blocks.md)

- [C またはC++ Symbols_in の __asm ブロックの使用](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [__asm ブロックの C または C++ のデータへのアクセス](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [インライン アセンブリでの関数の記述](../../assembler/inline/writing-functions-with-inline-assembly.md)

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>
