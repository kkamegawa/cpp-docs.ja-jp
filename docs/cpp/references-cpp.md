---
title: 参照 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
ms.openlocfilehash: 2353f0861f0f249416d0bb84a7a951b1cb6d64bc
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857334"
---
# <a name="references-c"></a>参照 (C++)

参照は、ポインターと同じように、メモリ内の他の場所に位置するオブジェクトのアドレスを格納します。 参照は、ポインターとは異なり、初期化された後で別のオブジェクトを参照するように指定したり、null に設定したりすることはできません。 参照には2種類あります。左辺値参照は、名前付き変数を参照し、右辺値参照は[一時オブジェクト](../cpp/temporary-objects.md)を参照します。 & 演算子は左辺値参照を示し、& & 演算子は、コンテキストに応じて右辺値参照またはユニバーサル参照 (右辺値または左辺値) を表します。

参照は次の構文を使用して宣言できます。

> \[*storage-class-specifiers*] \[*cv-qualifiers*] *type-specifiers* \[*ms-modifier*] *declarator* \[ **=** *expression*] **;**

参照を指定する任意の有効な宣言子を使用できます。 参照が関数または配列型への参照でない限り、次の簡略化された構文が適用されます。

> \[*ストレージクラス指定子*] \[*cv-修飾子*]*型指定子*\[ **&** または **&&** ] \[*cv-修飾子*]*識別子*\[ **=** *式*]) **;**

参照は次の順序で宣言します。

1. 宣言指定子:

   - ストレージ クラスの指定子 (省略可能)。

   - 省略可能な**const**や**volatile**修飾子。

   - 型指定子: 型の名前。

1. 宣言子:

   - オプションの Microsoft 固有の修飾子。 詳細については、「 [Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)」を参照してください。

   - **&** 演算子または **&&** 演算子。

   - 省略可能な**const**や**volatile**修飾子。

   - 識別子。

1. 初期化子 (省略可能)。

配列および関数へのポインターのより複雑な宣言子フォームは、配列および関数への参照にも適用されます。 詳細については、「[ポインター](../cpp/pointers-cpp.md)」を参照してください。

1 つの宣言指定子の後のコンマ区切りリストに、複数の宣言子と初期化子を含めることができます。 例:

```cpp
int &i;
int &i, &j;
```

次のように、参照、ポインター、およびオブジェクトをまとめて宣言できます。

```cpp
int &ref, *ptr, k;
```

参照は、オブジェクトのアドレスを保持しますが、構文的にはオブジェクトと同様に動作します。

次のプログラムでは、オブジェクトの名前 `s` とオブジェクトへの参照 `SRef` を、プログラム内で同じように使用できることに注意してください。

## <a name="example"></a>使用例

```cpp
// references.cpp
#include <stdio.h>
struct S {
   short i;
};

int main() {
   S  s;   // Declare the object.
   S& SRef = s;   // Declare the reference.
   s.i = 3;

   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);

   SRef.i = 4;
   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);
}
```

```Output
3
3
4
4
```

## <a name="see-also"></a>参照

[参照型関数の引数](../cpp/reference-type-function-arguments.md)<br/>
[参照型関数の戻り値](../cpp/reference-type-function-returns.md)<br/>
[ポインターへの参照](../cpp/references-to-pointers.md)
