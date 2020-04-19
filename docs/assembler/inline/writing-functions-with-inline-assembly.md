---
title: インライン アセンブリでの関数の記述
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 7848a8f071f50f8d809a999a96a9c0f8193c480e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166855"
---
# <a name="writing-functions-with-inline-assembly"></a>インライン アセンブリでの関数の記述

**Microsoft 固有の仕様**

インライン アセンブラー コードを持つ関数を記述する場合に、関数に引数を渡すし、これから値を返す簡単です。 次の例では、別のアセンブラーの最初に書き込まれ、インライン アセンブラーの再作成し、関数を比較します。 呼び出される関数は、`power2`は、最初のパラメーターを 2、2 番目のパラメーターの電源を掛けることの 2 つのパラメーターを受け取ります。 別のアセンブラー用に記述された、このよう関数になります。

```asm
; POWER.ASM
; Compute the power of an integer
;
       PUBLIC _power2
_TEXT SEGMENT WORD PUBLIC 'CODE'
_power2 PROC

        push ebp        ; Save EBP
        mov ebp, esp    ; Move ESP into EBP so we can refer
                        ;   to arguments on the stack
        mov eax, [ebp+4] ; Get first argument
        mov ecx, [ebp+6] ; Get second argument
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )
        pop ebp         ; Restore EBP
        ret             ; Return with sum in EAX

_power2 ENDP
_TEXT   ENDS
        END
```

別のアセンブラーに書き込まれるため、関数には、別のソース ファイルおよびアセンブリとリンクの手順が必要です。 通常、C および C++ の関数の引数はスタックに渡されますので、このバージョンの`power2`関数の引数はスタック上の位置にアクセスします。 (なお、**MODEL**ディレクティブ、MASM およびその他のいくつかのアセンブラーで使用可能では名前でのスタック引数とローカル スタック変数にアクセスすることもできます)。

## <a name="example"></a>例

このプログラムに書き込みます、`power2`関数インライン アセンブリ コード。

```cpp
// Power2_inline_asm.c
// compile with: /EHsc
// processor: x86

#include <stdio.h>

int power2( int num, int power );

int main( void )
{
    printf_s( "3 times 2 to the power of 5 is %d\n", \
              power2( 3, 5) );
}
int power2( int num, int power )
{
   __asm
   {
      mov eax, num    ; Get first argument
      mov ecx, power  ; Get second argument
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )
   }
   // Return with result in EAX
}
```

インライン バージョンの`power2`関数名では、引数を参照し、プログラムの残りの部分と同じソース ファイルに表示されます。 このバージョンでは、アセンブリ命令の数が少ないも必要です。

のインライン バージョン`power2`C は実行されません`return`ステートメントでは、無害な警告を発生ことには、警告レベル 2 またはそれ以降でコンパイルする場合。 関数は、値を返すには、コンパイラがない場合、`return`ステートメント。 使用することができます[#pragma warning](../../preprocessor/warning.md)この警告の生成を無効にします。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでの C または C++ の使用](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
