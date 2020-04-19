---
title: プロローグ/エピローグ コードの記述時の考慮事項
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: 52403fc45bbb68d693ef154bf39c5dd366dd10c5
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146483"
---
# <a name="considerations-when-writing-prologepilog-code"></a>プロローグ/エピローグ コードの記述時の考慮事項

**Microsoft 固有の仕様**

独自のプロローグとエピローグのコード シーケンスを記述する前に、スタック フレームがどのように配置されるかを理解することが重要です。**__LOCAL_SIZE** 事前定義済み定数の使用方法も知っておくと便利です。

##  <a name="_clang_c_stack_frame_layout"></a>C のスタック フレームのレイアウト

この例は、32 ビット関数で使用される標準プロローグ コードを示しています。

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

`localbytes` 変数は、ローカル変数のスタックで必要なバイト数を表します。また、`registers` 変数は、スタックに格納されるレジスタの一覧を表すプレースホルダーです。 レジスタをプッシュした後、スタックに他の適切なデータを配置できます。 対応するエピローグ コードは次のとおりです。

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

スタックは、常に下に (上位メモリ アドレスから下位メモリ アドレスに) 向かって大きくなります。 基本ポインター (`ebp`) は、プッシュされた `ebp` の値を指します。 ローカル変数領域は `ebp-2` から始まります。 ローカル変数にアクセスするには、`ebp` からのオフセットを計算します。そのためには、`ebp` から適切な値を減算します。

##  <a name="_clang_the___local_size_constant"></a>__LOCAL_SIZE 定数

コンパイラには、関数プロローグ コードのインライン アセンブラー ブロックで使用できる定数、**__LOCAL_SIZE** が用意されています。 この定数は、カスタム プロローグ コードでスタック フレームのローカル変数領域を割り当てるために使用されます。

**__LOCAL_SIZE** の値は、コンパイラによって決定されます。 値は、すべてのユーザー定義のローカル変数とコンパイラにより生成された一時変数の合計バイト数です。 **__LOCAL_SIZE** は、イミディエイト (即値) オペランドとしてのみ使用できます。式では使用できません。 この定数の値は、変更することも再定義することもできません。 次に例を示します。

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

カスタムのプロローグ シーケンスとエピローグ シーケンスを含む naked 関数の次の例では、プロローグ シーケンスで **__LOCAL_SIZE** を使用しています。

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[naked 関数](../c-language/naked-functions.md)
