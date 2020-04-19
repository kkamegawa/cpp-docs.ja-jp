---
title: コンパイラ エラー C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: ed4bc7eea85e5263d59817082caed99bde3d75d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353483"
---
# <a name="compiler-error-c2143"></a>コンパイラ エラー C2143

構文エラー: 'token2 'が見つかりましたする前に ' token1' がありません

コンパイラは、特定のトークン (空白以外の言語要素) が必要ですし、代わりにトークンが検出されました。

チェック、 [C++ 言語リファレンス](../../cpp/cpp-language-reference.md)コードが正しい構文を確認します。 コンパイラは、問題が発生する行を検出した後、このエラーを報告可能性があります、ため、エラーの前にいくつかの行のコードを確認します。

C2143 は、さまざまな状況で発生することができます。

演算子名を修飾することがときに起こる可能性 (`::`、 `->`、および`.`)、キーワードの後に`template`、この例のように。

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

C++ では既定では、想定される`Ty::PutFuncType`; テンプレートではありません、次にそのため、`<`小として解釈されます-記号。  必要がありますをコンパイラに指示明示的にいる`PutFuncType`テンプレートは、山かっして正しく解析できるようにします。 このエラーを修正するには、使用、`template`依存の型の名前を次に示すようにキーワード。

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143 が発生することがときに **/clr**使用と`using`ディレクティブは、構文エラー。

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

CLR の構文を使用しても使用せず、ソース コード ファイルをコンパイルしようとしているときに起こる可能性も **/clr**:

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

これに続く最初の空白以外の文字、`if`ステートメントは、左かっこをする必要があります。 コンパイラは、何を変換できません。

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

C2143 右中かっこ、かっこ、またはセミコロンが、エラーが検出された場所の行に不足している場合に発生したり、行の 1 つのすぐ上。

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

または、クラス宣言で無効なタグがある場合。

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

または、ラベルがステートメントにアタッチされていない場合。 場合を単独でラベルを配置する必要がありますなど、複合ステートメントの最後にアタッチ null ステートメント。

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

C++ 標準ライブラリ内の型を修飾なしの呼び出しが行われたときにエラーが発生します。

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

存在しないか`typename`キーワード。

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

または、明示的なインスタンス化を定義しようとする場合。

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

C プログラムで、関数の先頭に変数を宣言する必要があり、関数宣言以外の手順の実行後に宣言することはできません。

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
