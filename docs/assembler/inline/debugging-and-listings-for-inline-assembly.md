---
title: インライン アセンブリのデバッグと一覧表示
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 1b2ec146daf450c4302be9fea8fdd117ec6398da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167207"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>インライン アセンブリのデバッグと一覧表示

**Microsoft 固有の仕様**

使用してコンパイルする場合、ソース レベル デバッガーでインライン アセンブラー コードを格納しているプログラムをデバッグできる、 [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)オプション。

デバッガー内では、C または C++ とアセンブリ言語の両方の行にブレークポイントを設定できます。 混在アセンブリとソース モードを有効にした場合は、ソースとアセンブリ コードの逆アセンブルしたフォームの両方を表示できます。

複数のアセンブリ命令を配置することに注意してください。 または、ソース言語のステートメントを 1 つの行にデバッグの妨げになることができます。 元のモードでは、同じ行に個々 のステートメントではなく 1 つの行にブレークポイントを設定するのにデバッガーを使用できます。 同じ原則に適用されます、 `__asm` 、1 つの論理行に展開される C マクロとして定義されているブロックです。

混在ソースとアセンブリのリストを作成するかどうか、 [/FAs](../../build/reference/fa-fa-listing-file.md)コンパイラ オプションには、一覧には、アセンブリ言語の各行のソースとアセンブリの両方のフォームが含まれています。 一覧で、マクロは展開されませんが、コンパイル時に拡張されています。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでのアセンブリ言語の使用](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>