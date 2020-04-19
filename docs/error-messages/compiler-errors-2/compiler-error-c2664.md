---
title: コンパイラエラー C2664
ms.date: 11/04/2016
f1_keywords:
- C2664
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
ms.openlocfilehash: 93bdac489dea0356ce3da3298cd8ed6bcb6f623c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756007"
---
# <a name="compiler-error-c2664"></a>コンパイラエラー C2664

'function': 引数 n を 'type1' から 'type2' へ変換できません。

このパラメーター変換問題は、クラスのインスタンスが作成され、`explicit` キーワードでマークされたコンストラクターで暗黙的な変換が試みられた場合に生じる可能性があります。 明示的な変換の詳細については、「[ユーザー定義型変換](../../cpp/user-defined-type-conversions-cpp.md)」を参照してください。

パラメーターとしてオブジェクトへの参照を指定する関数に一時オブジェクトが渡される場合、その参照は `const` 参照である必要があります。

予測される以外の型のパラメーターが関数に渡されると、適切なコンストラクターを使用して一時オブジェクトが作成されます。 この一時オブジェクトは関数に渡されます。 この場合、一時オブジェクトは参照の初期化に使用されます。 旧バージョンの言語では、すべての参照を一時オブジェクトで初期化できました。

C2664 を解決するには、

- 指定された関数のプロトタイプを確認し、エラー メッセージに示された引数を修正してください。

- 必要に応じて、明示的な変換を指定してください。

クラスがそのベース クラスのいずれかにメンバーを隠ぺいした場合も、C2664 が生成されます。

詳細については、「[方法: System:: String を wchar_t * または char\*に変換する](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C2664 を生成し、その修正方法を示しています。

```cpp
// C2664.cpp
// C2664
struct A {
   void f(int i) {};
};

struct B : public A {
   // To fix, uncomment the following line.
   // using A::f;
   void f(A a) {};
};

int main() {
   B b;
   int i = 1;
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.
}
```

## <a name="example"></a>使用例

この例も、C2664 を生成し、その修正方法を示しています。

```cpp
// C2664b.cpp
// C2664 expected
struct A {
   // To fix, uncomment the following line.
   // A(int i){}
};

void func( int, A ) {}

int main() {
   func( 1, 1 );   // No conversion from int to A.
}
```

## <a name="example"></a>使用例

次の例では、`Test` を呼び出すリテラル文字列を使用して生成される C2664 と、その修正方法を示しています。 パラメーターは `szString` 参照であるため、適切なコンストラクターでオブジェクトが作成される必要があります。 結果は、参照の初期化に使用できない一時オブジェクトになります。

```cpp
// C2664c.cpp
// compile with: /EHsc
// C2664 expected
#include <iostream>
#include <string.h>
using namespace std;

class szString {
   int slen;
   char *str;

public:
   szString(const char *);
   int len() const {
      return slen;
   }
};

// Simple reference cannot bind to temp var.
void Test(szString &a) {}

// To fix, uncomment the following line.
// void Test(const szString &a) {}

szString::szString(const char * newstr) : slen(0), str(NULL) {
   slen=strlen(newstr);
   str = new char[slen + 1];
   if (str)
      strcpy_s(str, (slen + 1), newstr);
}

int main() {
   Test("hello");
}
```

## <a name="example"></a>使用例

`const` を適用するために C++ の標準要件が強制的に適用されます。 次の例では C2664 エラーが生成されます。

```cpp
// C2664d.cpp
// C2664 expected
#include <windows.h>

void func1(LPCSTR &s)
{

}

void func2(LPSTR &s)
{
   func1(s);
}

int main()
{
   return 0;
}
```

## <a name="example"></a>使用例

C2664 が生成されるより複雑な状況と、その修正方法を示します。

```cpp
// C2664e.cpp
// compile with: /EHsc
// C2664 expected
#define _INTL
#include <locale>
#include <iostream>

using namespace std;
#define LEN 90

int main( ) {
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));

   // To fix, delete the following line.
   char* pszNext;

   // To fix, uncomment the following line.
   // const char* pszNext;

   wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).in( state,
      pszExt, &pszExt[strlen(pszExt)], pszNext,
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   // See earlier comment.
      pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error) ?
                       L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;

   exit(-1);
}
```

## <a name="example"></a>使用例

関数呼び出しが満たされるように、列挙型変数はその基になる型に変換されません。 詳細については、「 [enum クラス](../../extensions/enum-class-cpp-component-extensions.md)」を参照してください。 次の例では、C2664 を生成し、その修正方法を示しています。

```cpp
// C2664f.cpp
// compile with: /clr
using namespace System;
public enum class A : Char {
   None = 0,
   NonSilent = 1,
};

void Test(Char c) {}

int main() {
   A aa = A::None;
   Test(aa);   // C2664
   Test(Char(aa));   // OK - fix by using a conversion cast
}
```

## <a name="example"></a>使用例

MIDL コンパイラのバグにより、wchar_t type は unsigned short として型ライブラリに出力されます。 このエラーを解決するには、型を C++ ソース コードにキャストするか、型を文字列として idl ファイルに定義します。

```
// C2664g.idl
import "prsht.idl";

[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]

interface IMyObj1 : IUnknown {
   HRESULT  teststr([in, string] wchar_t *wstr);
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);
   HRESULT  testbstr([in] BSTR bstr);
};

[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]
library myproj1 {
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]
   coclass CMyObj1 { interface IMyObj1; };
}
```

コードを Visual C++ 6.0 から新しいバージョンに移植するときに、`wchar_t` を使用しても C2664 が発生します。 Visual C++ 6.0 以前では、`wchar_t` は `typedef` の `unsigned short` であるため、その型に暗黙的に変換されます。 Visual C++ 6.0 より新しいバージョンでは、C++ 標準で指定されているように、`wchar_t` は独自の組み込み型で、`unsigned short` に暗黙的に変換されません。 「 [/Zc: wchar_t (Wchar_t はネイティブ型)」を](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)参照してください。

## <a name="example"></a>使用例

次の例では、C2664 を生成し、その修正方法を示しています。

```cpp
// C2664h.cpp
#import "C2664g.tlb"
using namespace myproj1;

int main() {
   IMyObj1Ptr ptr;

   wchar_t * mybuff = 0;
   BSTR bstr = 0;
   int len;
   ptr->teststr(mybuff);
   ptr->testbstr(bstr);
   ptr->testarr(mybuff, len);   // C2664
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast
}
```

## <a name="example"></a>使用例

C2664 は、コンパイラがテンプレートの引数を推定できない場合にも発生します。

```cpp
// C2664i.cpp
#include <stdio.h>
template <class T, int iType=0>
class CTypedImg {
public:
   CTypedImg() {}
   void run() {}

   operator CTypedImg<T>& () {
      return *((CTypedImg<T>*)this);
    }
};

template <class t1>
void test(CTypedImg<t1>& myarg) {
   myarg.run();
}

int main() {
   CTypedImg<float,2> img;

   test((CTypedImg<float>&)img);   // OK
   test<float>(img);   // OK
   test(img);   // C2664 - qualify as above to fix
}
```
