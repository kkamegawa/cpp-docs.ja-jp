---
title: インライン アセンブラーのラベルにジャンプ
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: 7653dc990e2f4b490bcbe333ed6f7586ac966d2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166907"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>インライン アセンブラーのラベルにジャンプ

**Microsoft 固有の仕様**

などの通常 C または C++ ラベルでは、ラベル、`__asm`ブロックは (ブロック) だけでなくで定義されているが、関数全体のスコープを持ちます。 アセンブリの両方の手順と`goto`ステートメントが内側または外側のラベルにジャンプできる、`__asm`ブロックします。

定義されているラベル`__asm`ブロックでは大文字と小文字両方;`goto`ステートメントおよびアセンブリ命令が小文字に関係なくそれらのラベルを参照できます。 C および C++ のラベルは大文字小文字を区別して使用する場合にのみ、`goto`ステートメント。 アセンブリ命令は、小文字に関係なく、C または C++ のラベルにジャンプできます。

次のコードは、すべての順列を示しています。

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

内のラベルとして C ライブラリの関数名を使用しない`__asm`ブロックします。 たとえばを使用したくなるかもしれません`exit`次のように、ラベルとして。

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

**exit**名前を指定しますこのコードは、C ライブラリ関数へのジャンプを発生する可能性があります、**exit**関数の代わりに目的の場所にします。

MASM のプログラム、ドル記号のように (`$`) は、現在の場所のカウンターとして機能します。 現在構成されている命令のラベルになります。 `__asm`ブロック、その主な用途は、時間の長い条件付きのジャンプを作成します。

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>
