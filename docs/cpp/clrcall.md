---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 6eb1a05eaf6669daa4cb7142ff16a57f7caf39cd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857607"
---
# <a name="__clrcall"></a>__clrcall

関数がマネージド コードからのみ呼び出されることを指定します。  マネージコードからのみ呼び出されるすべての仮想関数には **__clrcall**を使用します。 ただし、この呼び出し規則は、ネイティブ コードから呼び出される関数には使用できません。 **__Clrcall**修飾子は Microsoft 固有です。

マネージ関数から仮想マネージ関数への呼び出し時、またはポインターを使用してマネージ関数からマネージ関数への呼び出し時のパフォーマンスを向上させるには、 **__clrcall**を使用します。

エントリ ポイントはコンパイラが生成した個別の関数です。 関数にネイティブ エントリ ポイントとマネージド エントリ ポイントがある場合、そのいずれかが、関数実装を持つ実際の関数になります。 もう一方の関数は実際の関数に呼び出す別の関数 (サンク) で、共通言語ランタイムに PInvoke を実行させます。 関数を **__clrcall**としてマークする場合は、関数の実装が MSIL である必要があり、ネイティブエントリポイント関数が生成されないことを示します。

**__Clrcall**が指定されていない場合にネイティブ関数のアドレスを取得すると、コンパイラはネイティブエントリポイントを使用します。 **__clrcall**は、関数が管理されていて、マネージからネイティブへの遷移を実行する必要がないことを示します。 その場合、コンパイラはマネージド エントリ ポイントを使用します。

`/clr` (`/clr:pure` または `/clr:safe`) が使用されていて、 **__clrcall**が使用されていない場合、関数のアドレスを取得すると、常にネイティブエントリポイント関数のアドレスが返されます。 **__Clrcall**を使用した場合、ネイティブエントリポイント関数は作成されないため、エントリポイントサンク関数ではなく、マネージ関数のアドレスを取得します。 詳細については、「[ダブルサンキング](../dotnet/double-thunking-cpp.md)」を参照してください。 **/Clr: pure**および **/clr: safe**コンパイラオプションは visual studio 2015 で非推奨とされており、visual studio 2017 ではサポートされていません。

[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)は、すべての関数および関数ポインターが **__clrcall**ことを意味します。コンパイラは、コンパイル単位内の関数が **__clrcall**以外にマークされることを許可しません。 **/Clr: pure**を使用する場合、 **__clrcall**は関数ポインターと外部宣言に対してのみ指定できます。

関数に MSIL 実装がある限り、 C++ **/clr**を使用してコンパイルされた既存のコードから **__clrcall**関数を直接呼び出すことができます。 **__clrcall**関数は、インライン asm を持つ関数から直接呼び出すことはできません。また、たとえば、`/clr`を使用してコンパイルされた関数であっても、CPU 固有の依存関係を呼び出すことはできません。

**__clrcall**関数ポインターは、それらが作成されたアプリケーションドメインで使用することのみを目的としています。  アプリケーションドメイン間で **__clrcall**関数ポインターを渡す代わりに、<xref:System.CrossAppDomainDelegate>を使用します。 詳細については、「[アプリケーションドメインC++とビジュアル](../dotnet/application-domains-and-visual-cpp.md)」を参照してください。

## <a name="example"></a>使用例

関数が **__clrcall**で宣言されている場合は、必要に応じてコードが生成されることに注意してください。たとえば、関数が呼び出された場合などです。

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

## <a name="example"></a>使用例

次のサンプルでは、関数ポインターがマネージド コードからのみ呼び出されるように、関数ポインターを定義する方法を示します。 これにより、コンパイラはマネージド関数を直接呼び出し、ネイティブ エントリ ポイント (ダブル サンクの問題) を避けることができます。

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>参照

[引数の渡し規則と名前付け規則](../cpp/argument-passing-and-naming-conventions.md)<br/>
[キーワード](../cpp/keywords-cpp.md)
