---
title: 非推奨 (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: 34f9c10cd898b0359463d5933141822576fa4a11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398954"
---
# <a name="deprecated-c"></a>非推奨 (C++)

このトピックでは、Microsoft 固有について declspec 宣言を非推奨とされます。 C++ 14 について`[[deprecated]]`属性、および Microsoft 固有の declspec またはプラグマとその属性を使用するタイミングに関するガイダンスを参照してください。 [C++ の標準属性](attributes.md)します。

例外については、下、**非推奨とされます**宣言と同じ機能を提供する、[非推奨とされます](../preprocessor/deprecated-c-cpp.md)プラグマ。

- **非推奨とされます**宣言により、非推奨として特定の形式の関数のオーバー ロードを指定する一方、プラグマ形式はすべてのオーバー ロードされた関数名に適用されます。

- **非推奨とされます**宣言では、コンパイル時に表示されるメッセージを指定することができます。 このメッセージのテキストをマクロから取り込むことができます。

- マクロは非推奨とされたとしてマークされているのみ、**非推奨とされます**プラグマ。

コンパイラが非推奨の識別子または標準の使用を検出するかどうかは[ `[[deprecated]]` ](attributes.md)属性、 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)警告がスローされます。

## <a name="example"></a>例

次の例では、関数を非推奨としてマークする方法、および非推奨の関数が使用されている場合、コンパイル時に表示されるメッセージを指定する方法を示します。

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

## <a name="example"></a>例

次の例では、クラスを非推奨としてマークする方法、および非推奨のクラスが使用されている場合、コンパイル時に表示されるメッセージを指定する方法を示します。

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)