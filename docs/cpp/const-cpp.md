---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: 759ee503acb12f6c1a30fbbfaf87a8f66433e571
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154751"
---
# <a name="const-c"></a>const (C++)

データの宣言を変更するときに、 **const**キーワードは、オブジェクトまたは変数に変更がないを指定します。

## <a name="syntax"></a>構文

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>const の値

**Const**キーワードは、変数の値は定数であり、コンパイラは、プログラマがこれを変更できないようにすることを指定します。

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

C++ では、使用することができます、 **const**キーワードの代わりに、 [#define](../preprocessor/hash-define-directive-c-cpp.md)プリプロセッサ ディレクティブの定数値を定義します。 定義された値**const**型がチェックされる可能性があり、定数式の代わりに使用できます。 C++ では、使用して配列のサイズを指定することができます、 **const**変数として次のとおりです。

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

C では、定数値は既定で外部リンケージに設定されるため、ソース ファイルでのみ指定できます。 C++ では、定数値は既定で内部リンケージに設定されるため、ヘッダー ファイルで指定できます。

**Const**ポインター宣言でキーワードを使用することもできます。

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

として宣言された変数へのポインター **const**としても宣言されているポインターにのみ割り当てることができます**const**します。

```cpp
// constant_values4.cpp
#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf;   // Pointer to constant data
   printf_s("%s\n", bptr);

   // *bptr = 'a';   // Error
}
```

定数データへのポインターを関数パラメーターとして使用して、ポインターを通じて渡されるパラメーターが関数によって変更されないようにすることができます。

として宣言されているオブジェクトの**const**、できるだけ定数メンバー関数を呼び出します。 これによって、定数オブジェクトは変更されなくなります。

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

非定数オブジェクトに対して、定数または非定数のメンバー関数を呼び出すことができます。 使用してメンバー関数をオーバー ロードできますも、 **const**キーワードです。 これにより、別のバージョンの定数および非定数オブジェクトに対して呼び出される関数。

コンス トラクターまたはデストラクターを宣言することはできません、 **const**キーワード。

## <a name="const-member-functions"></a>const のメンバー関数

メンバー関数を宣言すること、 **const**キーワードは、関数が呼び出されたオブジェクトを変更しない「読み取り専用」関数であるを指定します。 定数メンバー関数は、非静的データ メンバーを変更またはメンバー定数でない関数を呼び出すことはできません。定数メンバー関数を宣言するには、配置、 **const**引数リストのかっこの後のキーワード。 **Const**宣言と定義の両方のキーワードが必要です。

```cpp
// constant_member_function.cpp
class Date
{
public:
   Date( int mn, int dy, int yr );
   int getMonth() const;     // A read-only function
   void setMonth( int mn );   // A write function; can't be const
private:
   int month;
};

int Date::getMonth() const
{
   return month;        // Doesn't modify anything
}
void Date::setMonth( int mn )
{
   month = mn;          // Modifies data member
}
int main()
{
   Date MyDate( 7, 4, 1998 );
   const Date BirthDate( 1, 18, 1953 );
   MyDate.setMonth( 4 );    // Okay
   BirthDate.getMonth();    // Okay
   BirthDate.setMonth( 4 ); // C2662 Error
}
```

## <a name="c-and-c-const-differences"></a>C および C++ の const の相違点

として変数を宣言するときに**const** C ソース コード ファイルでこれを行うとします。

```cpp
const int i = 2;
```

そして、次のように、この変数を別のモジュールで使用できます。

```cpp
extern const int i;
```

C++ で同じ動作を取得することを宣言する必要があります、 **const**変数として。

```cpp
extern const int i = 2;
```

宣言する場合、 **extern** C ソース コード ファイルの使用で使用するためには、C++ ソース コード ファイルで変数。

```cpp
extern "C" const int x=10;
```

C++ コンパイラによる名前修飾を防止します。

## <a name="remarks"></a>Remarks

次のメンバー関数のパラメーター リストでは、ときに、 **const**キーワードは、関数が呼び出されたオブジェクトを変更しないことを指定します。

詳細については**const**、次のトピックを参照してください。

- [const ポインターと volatile ポインター](../cpp/const-and-volatile-pointers.md)

- [型修飾子 (C 言語リファレンス)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)