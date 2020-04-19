---
title: インライン アセンブラーの概要
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 21e0d9ca0e64922b83518eb79c19d2f2e67813bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167012"
---
# <a name="inline-assembler-overview"></a>インライン アセンブラーの概要

**Microsoft 固有の仕様**

インライン アセンブラーを使用して、アセンブリとリンクの追加手順なしの C および C++ ソース プログラムにアセンブリ言語命令を埋め込むことができます。 インライン アセンブラーは、コンパイラに組み込まれます。したがって、MASM (Microsoft Macro Assembler) などの別のアセンブラーは必要ではありません。

インライン アセンブラーは別のアセンブリとリンクの手順を必要としないので、別のアセンブラーより便利です。 インライン アセンブリ コードは、C または C++ 変数または関数の名前は、プログラムの C および C++ コードと統合しやすいように、スコープ内を使用できます。 およびが困難または不可能な C または C++ だけでタスクを実行できるため、C および C++ のステートメントで、アセンブリ コードを混在させることができます。

[_ _Asm](../../assembler/inline/asm.md)キーワードは C の場所に表示されることができますをインライン アセンブラーを呼び出しまたはC++ステートメントが有効です。 これは、単独では使用できません。 アセンブリ命令、中かっこで囲まれた命令グループ、または少なくとも空の中かっこの後で指定する必要があります。 "`__asm` ブロック" という用語は、ここでは、中かっこに囲まれているかどうかを問わず、命令または命令のグループを示します。

次のコードは、単純な`__asm`中かっこで囲まれたブロックします。 (コードは、カスタム関数プロローグ シーケンスです)。

```cpp
// asm_overview.cpp
// processor: x86
void __declspec(naked) main()
{
    // Naked functions must provide their own prolog...
    __asm {
        push ebp
        mov ebp, esp
        sub esp, __LOCAL_SIZE
    }

    // ... and epilog
    __asm {
        pop ebp
        ret
    }
}
```

または、各アセンブリ命令の前に `__asm` を置くことができます。

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

`__asm` キーワードはステートメント区切り文字であるため、アセンブリ命令も同じ行に記述できます。

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>