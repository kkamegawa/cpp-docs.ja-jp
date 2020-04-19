---
title: __asm ブロックの C または C++ のデータへのアクセス
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: 1f56cc5c049c1501ea09c76f31be3ab9dea5ed10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167609"
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>__asm ブロックの C または C++ のデータへのアクセス

**Microsoft 固有の仕様**

インライン アセンブリの非常に便利では、C または C++ の変数名で参照する機能です。 `__asm`ブロックできるブロックが表示されているスコープ内の変数の名前も含め、任意のシンボルを参照してください。 たとえば場合、C 変数`var`スコープ、命令では、

```cpp
__asm mov eax, var
```

値を格納`var`EAX にします。

クラス、構造体または共用体のメンバーに一意の名前がある場合、`__asm`ブロックが、変数を指定せず、メンバーの名前のみを使用して参照できますまたは`typedef`ピリオドの前に、の名前 (**.**) 演算子。 メンバー名が一意でない場合、配置する必要あります変数または`typedef`期間の演算子の直前の名前。 次のサンプル共有の構造体の型など、`same_name`メンバー名として: です。

型と変数を宣言する場合

```cpp
struct first_type hal;
struct second_type oat;
```

すべての参照のメンバーに`same_name`ために、変数名を使用する必要があります`same_name`一意ではありません。 メンバーが、`weasel`一意の名前を持つメンバー名のみを使用して参照できるようにします。

```cpp
// InlineAssembler_Accessing_C_asm_Blocks.cpp
// processor: x86
#include <stdio.h>
struct first_type
{
   char *weasel;
   int same_name;
};

struct second_type
{
   int wonton;
   long same_name;
};

int main()
{
   struct first_type hal;
   struct second_type oat;

   __asm
   {
      lea ebx, hal
      mov ecx, [ebx]hal.same_name ; Must use 'hal'
      mov esi, [ebx].weasel       ; Can omit 'hal'
   }
   return 0;
}
```

変数名を省略することはだけのためのコーディングであることに注意してください。 変数名が存在するかどうかは、同じアセンブリ命令が生成されます。

アクセスの制限に関係なく C++ でのデータ メンバーにアクセスできます。 ただし、関数メンバーを呼び出すことはできません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでの C または C++ の使用](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>