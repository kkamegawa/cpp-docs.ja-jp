---
title: __asm ブロックの C マクロとしての定義
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: c48298cf802600995dbbf68885896b6feccb807d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167027"
---
# <a name="defining-asm-blocks-as-c-macros"></a>__asm ブロックの C マクロとしての定義

**Microsoft 固有の仕様**

C マクロは、ソース コードにアセンブリのコードを挿入する便利な手段を提供しますが、マクロの展開を 1 論理行にいるため、特に注意を要求します。 問題のないマクロを作成するには、これらの規則に従います。

- 囲む、`__asm`中かっこでブロックします。

- 配置、`__asm`各アセンブリ命令の前にキーワード。

- 旧式の C コメントを使用して ( `/* comment */`) アセンブリ スタイルのコメントではなく ( `; comment`) または C の単一行コメント ( `// comment`)。

を示すためには、次の例は、単純なマクロを定義します。

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

一見、最後の 3 つ`__asm`キーワードが余分なようです。 必要なただし、マクロの 1 行に展開するため。

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

3 番目と 4 番目`__asm`キーワードはステートメント区切り文字として必要です。 唯一のステートメント区切り文字が認識される`__asm`ブロックは、改行文字と`__asm`キーワード。 各命令を区切る必要があります、マクロとして定義されているブロックが 1 つの論理行であるため、`__asm`します。

中かっこはも不可欠です。 これらを省略した場合、コンパイラはマクロ呼び出しの右側に同じ行の C または C++ ステートメントによって混乱することができます。 アセンブリ コードが停止して、終わりかっこなし、コンパイラがわかりません C または C++ ステートメントを表示した後、`__asm`アセンブリ命令としてブロックされます。

セミコロンで始まるアセンブリ スタイルのコメント (**;**)、行の最後まで続行します。 コンパイラは論理行の末尾に至る、コメントの後にすべてを無視するためのマクロの問題が発生します。 単一行の C または C++ のコメントのも同様です ( `// comment`)。 エラーを防ぐためには、旧式の C のコメントを使用して、( `/* comment */`) で`__asm`ブロックがマクロとして定義します。

`__asm`ブロックの C マクロは引数を受け取ることができますと書き込まれます。 通常 C マクロをただしとは異なり、`__asm`マクロが値を返すことはできません。 このため、C または C++ の式では、このようなマクロを使用することはできません。

この種類のマクロを呼び出す無秩序しないように注意します。 たとえばで宣言された関数で、アセンブリ言語のマクロを呼び出す、`__fastcall`規則予期しない結果が発生する可能性があります。 (を参照してください[の使用およびインライン アセンブリでのレジスタに保持](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md))。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>