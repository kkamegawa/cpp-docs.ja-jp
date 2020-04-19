---
title: ヘッダーファイル (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: ca5036ee53372f44e53b5a6452d4ab220fc3977d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301484"
---
# <a name="header-files-c"></a>ヘッダーファイル (C++)

変数、関数、クラスなどのプログラム要素の名前は、使用する前に宣言する必要があります。 たとえば、最初に ' x ' を宣言せずに `x = 42` を作成することはできません。

```cpp
int x; // declaration
x = 42; // use x
```

宣言は、要素が**int**、 **double**、**関数**、**class**、またはその他のものであるかどうかをコンパイラに指示します。  また、各名前は、使用されるすべての .cpp ファイルで (直接または間接的に) 宣言される必要があります。 プログラムをコンパイルすると、各 .cpp ファイルはコンパイル単位に個別にコンパイルされます。 コンパイラは、他のコンパイル単位で宣言されている名前を認識しません。 つまり、クラス、関数、またはグローバル変数を定義する場合は、それを使用する追加の .cpp ファイルごとに、その変数の宣言を指定する必要があります。 各宣言は、すべてのファイルでまったく同じである必要があります。 不整合がわずかであると、リンカーがすべてのコンパイルユニットを1つのプログラムにマージしようとしたときに、エラーまたは意図しない動作が発生します。

エラーが発生する可能性を最小限C++に抑えるため、では、宣言を含む*ヘッダーファイル*を使用するという慣例が採用されています。 ヘッダーファイルで宣言を行い、その宣言を必要とするすべての .cpp ファイルまたはその他のヘッダーファイルで #include ディレクティブを使用します。 #Include ディレクティブは、コンパイルの前にヘッダーファイルのコピーを .cpp ファイルに直接挿入します。

> [!NOTE]
> Visual Studio 2019 では、C++ 20*モジュール*機能が改善され、ヘッダーファイルの最終的な置換として導入されました。 詳細については、「」の「 [ C++モジュールの概要](modules-cpp.md)」を参照してください。

## <a name="example"></a>使用例

次の例は、クラスを宣言し、別のソースファイルで使用する一般的な方法を示しています。 まず、ヘッダーファイルの `my_class.h`を使用します。 これにはクラス定義が含まれていますが、定義が不完全であることに注意してください。メンバー関数 `do_something` が定義されていません。

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

次に、実装ファイルを作成します (通常は .cpp または同様の拡張機能を使用します)。 ファイル my_class を呼び出し、メンバー宣言の定義を指定します。 .Cpp ファイルのこの位置に my_class 宣言を挿入するには、"my_class .h" ファイルの `#include` ディレクティブを追加します。また、`std::cout`の宣言を取得する `<iostream>` を含めます。 ソースファイルと同じディレクトリにあるヘッダーファイルには引用符が使用され、標準ライブラリのヘッダーには山かっこが使用されていることに注意してください。 また、標準ライブラリの多くのヘッダーには、.h またはその他のファイル拡張子はありません。

実装ファイルでは、必要に応じて using ステートメントを使用**して**、"my_class" または "cout" というすべての言及を "N::" または "std::" で修飾する必要がないようにすることができます。  ヘッダーファイルには**using ステートメントを**入れないでください。

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

これで、別の .cpp ファイルで `my_class` を使用できるようになりました。 コンパイラが宣言内を取り込むように、ヘッダーファイルを #include します。 コンパイラは、my_class が `do_something()`と呼ばれるパブリックメンバー関数を持つクラスであることを認識している必要があります。

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

コンパイラは、各 .cpp ファイルを .obj ファイルにコンパイルし終えると、.obj ファイルをリンカーに渡します。 リンカーがオブジェクトファイルをマージすると、my_class の定義が1つだけ検出されます。これは my_class .cpp 用に生成された .obj ファイルにあり、ビルドは成功します。

## <a name="include-guards"></a>ガードを含める

通常、ヘッダーファイルには、1つの .cpp ファイルに複数回挿入されないように、ガードまたは `#pragma once` ディレクティブが*含ま*れています。

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>ヘッダーファイルに格納する内容

ヘッダーファイルは複数のファイルに含まれる可能性があるため、同じ名前の複数の定義を生成する可能性のある定義を含めることはできません。 次のものは使用できません。また、非常に悪い方法であると考えられます。

- 名前空間またはグローバルスコープでの組み込み型の定義
- 非インライン関数定義
- 非 const 変数の定義
- 集計の定義
- 名前のない名前空間
- using ディレクティブ

**Using**ディレクティブを使用すると、必ずしもエラーが発生するとは限りませんが、そのヘッダーを直接または間接的にインクルードするすべての .cpp ファイルのスコープに名前空間が含まれるため、問題が発生する可能性があります。

## <a name="sample-header-file"></a>サンプルヘッダーファイル

次の例は、ヘッダーファイルで許可されているさまざまな種類の宣言と定義を示しています。

```cpp
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```
