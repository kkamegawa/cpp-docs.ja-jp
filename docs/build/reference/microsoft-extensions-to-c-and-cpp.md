---
title: C および C++ の Microsoft 拡張機能
ms.date: 06/14/2018
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
ms.openlocfilehash: dab8ac23be8b66ca84c57514c6c04e94dddebaae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321190"
---
# <a name="microsoft-extensions-to-c-and-c"></a>C および C++ の Microsoft 拡張機能

Visual C++ は、ANSI C および ANSI C++ 標準を次のように拡張します。

## <a name="keywords"></a>キーワード

複数のキーワードが追加されます。 一覧で[キーワード](../../cpp/keywords-cpp.md)、先頭 2 つのアンダー スコアがあるキーワードは、Visual C の拡張機能。

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>静的 const の整数型 (または列挙型) のメンバーのクラス定義外

標準 (**/Za**)、次のように、データ メンバーの場合、クラスの定義を行う必要があります。

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

**/Ze**クラスの定義は静的で定数の型の整数および列挙データ メンバーの省略可能です。 クラス内に初期化子を持つことができるのは、静的で定数型の整数と列挙だけです。初期化式には、定数型の式を使用する必要があります。

使用して、クラスの定義がヘッダーでファイルとヘッダー ファイルが含まれている複数のソース ファイルで提供されるときにエラーを回避する[selectany](../../cpp/selectany.md)します。 例:

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>キャスト

C++ コンパイラおよび C コンパイラは、次の種類の非 ANSI キャストをサポートします。

- 左辺値を生成するための非 ANSI キャスト。 例えば:

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > この拡張機能は、C 言語でのみ使用できます。 C++ コードで次の ANSI C 標準形式を使用して、ポインターを別の型へのポインターであるかのように変更できます。

   この例を次のように書き換えると、ANSI C 規格に準拠します。

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- 関数ポインターからデータ ポインターへの非 ANSI キャスト。 例えば:

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   上の例と同じキャストを行い、ANSI 規格に準拠させるには、次に示すように関数ポインターをまず `uintptr_t` 型にキャストし、その後データ ポインターにキャストします。

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>可変長引数リスト

C++ および C コンパイラでは、可変個の引数を指定する関数宣言子を使用できます。その後ろには、型を指定する関数定義を記述します。

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>単一行コメント

C コンパイラでは、次のように 2 つのスラッシュ (//) で始まる単一行コメントがサポートされています。

```C
// This is a single-line comment.
```

## <a name="scope"></a>スコープ

C コンパイラでは、次のようなスコープ関連のコードを記述できます。

- extern を static として再定義する。

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- 同じスコープ内で typedef 定義を複数回記述する。

   ```C
   typedef int INT;
   typedef int INT;
   ```

- 関数宣言子をファイル スコープにする。

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- 非定数式で初期化したブロック スコープ変数を使用する。

   ```C
   int clip( int );
   int bar( int );
   int main( void )
   {
       int array[2] = { clip( 2 ), bar( 4 ) };
   }
   int clip( int x )
   {
       return x;
   }
   int bar( int x )
   {
       return x;
   }
   ```

## <a name="data-declarations-and-definitions"></a>データの宣言と定義

C コンパイラでは、以下のデータ宣言およびデータ定義の機能をサポートしています。

- 初期化子内に文字定数と文字列定数を混在させる。

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- ビット フィールド以外の基本型を持つ**符号なし int**または**int を署名**します。

- 型がない宣言子:

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- 可変長配列を構造体および共用体の最後のフィールドとして指定する。

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- 名前のない (無名) 構造体を使用する。

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- 名前のない (無名) 共用体を使用する。

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- 名前のないメンバーを使用する。

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>浮動小数点の組み込み関数

両方 x86 C++ コンパイラおよび C コンパイラのインライン生成をサポート、 `atan`、 `atan2`、 `cos`、 `exp`、 `log`、 `log10`、 `sin`、 `sqrt`、および`tan`関数と **/Oi**を指定します。 C コンパイラの場合、これらの組み込みでは `errno` 変数が設定されないため、ANSI に準拠しなくなります。

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Const ポインター パラメーターへの参照を関数に非 const ポインター パラメーターを渡すことが必要です。

これは C++ の拡張機能です。 このコードはコンパイルで **/Ze**:

```cpp
typedef   int   T;

const T  acT = 9;      // A constant of type 'T'
const T* pcT = &acT;   // A pointer to a constant of type 'T'

void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'
{
   rpcT = pcT;
}

T*   pT;               // A pointer to a 'T'

void func ()
{
   func2 ( pT );      // Should be an error, but isn't detected
   *pT   = 7;         // Invalidly overwrites the constant 'acT'
}
```

## <a name="iso646h-not-enabled"></a>ISO646 します。H は有効になっていません

**/Ze**、表示形式は次の演算子を使用する場合は、iso646.h をインクルードする必要があります。

- & & (および)

- & = (and_eq)

- (& a) (bitand)

- &#124;(bitor)

- ~ (compl)

- ! (not)

- != (not_eq)

- &#124;&#124;(または)

- &#124;= (or_eq)

- ^ (xor)

- ^= (xor_eq)

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>文字列リテラルのアドレスが型 const char でない const char (*)

次の例の出力は`char const (*)[4]` **/Za**が`char const [4]` **/Ze**します。

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>関連項目

- [/Za、/Ze (言語拡張機能の無効化)](za-ze-disable-language-extensions.md)
- [MSVC コンパイラ オプション](compiler-options.md)
- [MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
