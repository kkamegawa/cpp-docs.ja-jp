---
title: コンパイラの警告 (レベル 3 および 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: a12bee4591df8a7a952dc741c4b26c637bb5256c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991078"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>コンパイラの警告 (レベル 3 および 4) C4244

'conversion': 'type1' から 'type2' に変換しました。データが失われている可能性があります。

整数型が、より小さい整数の型に変換されています。 Type1*が `int` 場合、および* *type1*が `int`よりも小さい場合、これはレベル4の警告です。 それ以外の場合は、レベル 3 (`unsigned int`型の変数に[__int64](../../cpp/int8-int16-int32-int64.md)型の値が割り当てられます) です。 データが失われた可能性があります。

C4244 の場合は、互換性のある型を使用するようにプログラムを変更するか、別のロジックをコードに追加して、変換される値の範囲が使用している型と常に互換性があるようにします。

C4244 は、レベル2でも発生する可能性があります。詳細については、「[コンパイラの警告 (レベル 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) 」を参照してください。

変換では、暗黙の変換によって問題が発生する可能性があります。

次の例では C4244 が生成されます。

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

詳細については、「[通常の算術変換](../../c-language/usual-arithmetic-conversions.md)」を参照してください。

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

警告 C4244 は、64 ビット ターゲットのコードをビルドする際に発生することがあり、32 ビット ターゲットのビルドでは発生しません。 たとえば、ポインター間の違いは、32 ビット プラットフォームでは 32 ビット数で、64 ビット プラットフォームでは 64 ビット数ということです。

次の例では、64 ビット ターゲットのコンパイル時に C4244 が生成されます。

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```
