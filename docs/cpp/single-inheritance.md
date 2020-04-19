---
title: 単一継承
ms.date: 11/19/2018
helpviewer_keywords:
- single inheritance
- base classes [C++], indirect
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- derived classes [C++], single base class
- inheritance, single
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
ms.openlocfilehash: 96af0c42a32f14280fd8c208a3e4eaec38a8ca3a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331123"
---
# <a name="single-inheritance"></a>単一継承

継承の一般的な形態である "単一継承" では、クラスの持つ基底クラスは 1 つだけです。 次の図に示す関係を考えます。

![1 つの基本的な&#45;継承グラフ](../cpp/media/vc38xj1.gif "基本的な単一&#45;継承グラフ") <br/>
単純な単一継承のグラフ

図における一般から特殊への流れに注意してください。 ほとんどのクラス階層のデザインにあるもう 1 つの一般的な属性は、派生クラスが基底クラスと "kind of" (種類) 関係を持つことです。 図では、`Book` は `PrintedDocument` の 1 種であり、`PaperbackBook` は `book` の 1 種です。

図でもう 1 つ注意する必要があるのは、`Book` が派生クラス (`PrintedDocument` から派生) であると同時に基底クラス (`PaperbackBook` は `Book` から派生) でもあるという点です。 このようなクラス階層の骨格となる宣言を次の例に示します。

```cpp
// deriv_SingleInheritance.cpp
// compile with: /LD
class PrintedDocument {};

// Book is derived from PrintedDocument.
class Book : public PrintedDocument {};

// PaperbackBook is derived from Book.
class PaperbackBook : public Book {};
```

`PrintedDocument` は `Book` の "直接基底" クラスと見なされます。これは `PaperbackBook` の "間接基底" クラスです。 違いは、直接基底クラスがクラス宣言の基底クラスのリストに記述され、間接基底クラスはそうでないことです。

各クラスが派生される基底クラスは、派生クラスを宣言する前に宣言されています。 基底クラスについて前方参照の宣言を指定するだけでは十分ではありません。完全な宣言である必要があります。

前の例では、アクセス指定子で**public**使用されます。 public、protected、および private の継承の意味については、「[メンバー アクセス コントロール。](../cpp/member-access-control-cpp.md)

クラスは、次の図に示すように、多くの特定のクラスの基底クラスとして機能します。

![指示に従って有向非巡回グラフ](../cpp/media/vc38xj2.gif "ダイレクト有向非巡回グラフ") <br/>
有向非循環グラフの例

"有向非循環グラフ" ("DAG") と呼ばれる上記の図では、一部のクラスが複数の派生クラスの基底クラスになっています。 ただし、その逆は正しくありません。どの派生クラスにも直接基底クラスは 1 つしかありません。 図のグラフは、"単一継承" 構造を示しています。

> [!NOTE]
> 有向非循環グラフは、単一継承に特有のものではありません。 多重継承グラフを記述するためにも使用されます。

継承の場合、派生クラスは、基底クラスのメンバーと、追加した新しいメンバーを含みます。 その結果、派生クラスは基底クラスのメンバーを参照できます (それらのメンバーが派生クラスで再定義されていない限り)。 直接または間接基底クラスのメンバーが派生クラスで再定義された場合は、スコープ解決演算子 (`::`) を使用してそれらのメンバーを参照できます。 次の例について考えます。

```cpp
// deriv_SingleInheritance2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;
class Document {
public:
   char *Name;   // Document name.
   void PrintNameOf();   // Print name.
};

// Implementation of PrintNameOf function from class Document.
void Document::PrintNameOf() {
   cout << Name << endl;
}

class Book : public Document {
public:
   Book( char *name, long pagecount );
private:
   long  PageCount;
};

// Constructor from class Book.
Book::Book( char *name, long pagecount ) {
   Name = new char[ strlen( name ) + 1 ];
   strcpy_s( Name, strlen(Name), name );
   PageCount = pagecount;
};
```

`Book` のコンストラクター (`Book::Book`) はデータ メンバー `Name` にアクセスできることに注意してください。 プログラムでは、`Book` 型のオブジェクトは次のように作成して使用できます。

```cpp
//  Create a new object of type Book. This invokes the
//   constructor Book::Book.
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );

...

//  Use PrintNameOf function inherited from class Document.
LibraryBook.PrintNameOf();
```

前の例で示したように、クラス メンバーおよび継承されたデータと関数は同じように使用されます。 `Book` クラスの実装で `PrintNameOf` 関数の再実装が必要である場合、`Document` クラスに属する関数はスコープ解決演算子 (`::`) を使用することによってのみ呼び出すことができます。

```cpp
// deriv_SingleInheritance3.cpp
// compile with: /EHsc /LD
#include <iostream>
using namespace std;

class Document {
public:
   char *Name;          // Document name.
   void  PrintNameOf() {}  // Print name.
};

class Book : public Document {
   Book( char *name, long pagecount );
   void PrintNameOf();
   long  PageCount;
};

void Book::PrintNameOf() {
   cout << "Name of book: ";
   Document::PrintNameOf();
}
```

アクセス可能であいまいでない基底クラスが存在している場合、派生クラスへのポインターと参照は、その基底クラスへのポインターと参照に暗黙的に変換できます。 次のコードは、ポインターを使用して、この概念を示しています (同じ原則が参照にも適用されます)。

```cpp
// deriv_SingleInheritance4.cpp
// compile with: /W3
struct Document {
   char *Name;
   void PrintNameOf() {}
};

class PaperbackBook : public Document {};

int main() {
   Document * DocLib[10];   // Library of ten documents.
   for (int i = 0 ; i < 5 ; i++)
      DocLib[i] = new Document;
   for (int i = 5 ; i < 10 ; i++)
      DocLib[i] = new PaperbackBook;
}
```

前の例では、異なる型が作成されます。 ただし、これらの型はすべて `Document` クラスから派生しているため、`Document *` への暗黙の型変換が実行されます。 その結果、`DocLib` は、異なる種類のオブジェクトを含む "異種混在リスト" (すべてのオブジェクトが同じ型ではないリスト) です。

`Document` クラスには `PrintNameOf` 関数があるため、ライブラリの各ブックの名前を出力できますが、ドキュメントの型に固有の情報の一部 (`Book` のページ番号、`HelpFile` のバイト数など) が省略される可能性があります。

> [!NOTE]
>  基底クラスで `PrintNameOf` のような関数の実装を強制するのは、多くの場合、最適なデザインではありません。 [仮想関数](../cpp/virtual-functions.md)設計の他の手段を提供します。