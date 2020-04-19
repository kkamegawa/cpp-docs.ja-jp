---
title: メンバーへのポインター
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: 14b5c12715d1c4c27d9ef8e262170acb2f85e526
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857347"
---
# <a name="pointers-to-members"></a>メンバーへのポインター

メンバーへのポインターの宣言は、ポインター宣言の特殊なケースです。  これらは次のシーケンスで宣言します。

```
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]qualified-name ::* [cv-qualifiers] identifier
[= & qualified-name :: member-name];
```

1. 宣言指定子:

   - ストレージ クラスの指定子 (省略可能)。

   - 省略可能な**const**や**volatile**指定子。

   - 型指定子: 型の名前。  これは指されるメンバーのクラスではなく、種類です。

1. 宣言子:

   - オプションの Microsoft 固有の修飾子。 詳細については、「 [Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)」を参照してください。

   - 指されるメンバーが含まれるクラスの修飾名。

   - __::__ 演算子。

   - __\*__ 演算子。

   - 省略可能な**const**や**volatile**指定子。

   - メンバーへのポインターを指定する識別子。

1. 初期化子 (省略可能):

   - **=** 演算子。

   - **&** 演算子。

   - クラスの修飾名。

   - __::__ 演算子。

   - 適切な型のクラスの非静的メンバーの名前。

当然ながら、1 つの宣言で複数の宣言子 (および関連する初期化子) を使用できます。

クラスのメンバーへのポインターは、メンバーの型およびメンバーが属するクラスの情報を持つ点で通常のポインターとは異なります。 通常のポインターは、メモリ内の 1 つのオブジェクトだけを識別します (1 つのオブジェクトのアドレスだけを持ちます)。 クラスのメンバーへのポインターは、クラスのインスタンスのメンバーを識別します。 次の例では、`Window` クラス、およびメンバー データへのポインターをいくつか宣言します。

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

前の例では、`pwCaption` は型 `char*`を持つクラス `Window` のメンバーへのポインターです。 `pwCaption` の型は `char * Window::* ` です。 次のコードでは、メンバー関数 `SetCaption` および `GetCaption` へのポインターを宣言します。

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

ポインター `pfnwGC` および `pfnwSC` はそれぞれ、`GetCaption` クラスの `SetCaption` および `Window` を指します。 次のコードは、メンバー `pwCaption` へのポインターを使用してウィンドウ キャプションに情報を直接コピーします。

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

との差 **。** <strong>\*</strong>および **->** <strong>\*</strong>演算子 (メンバーへのポインター演算子) は、**です。** <strong>\*</strong>演算子は、オブジェクト参照またはオブジェクト参照を指定してメンバーを選択します。一方、 **->** <strong>\*</strong>演算子は、ポインターを介してメンバーを選択します。 (これらの演算子の詳細については、「[メンバーへのポインター演算子を使用した式](../cpp/pointer-to-member-operators-dot-star-and-star.md)」を参照してください)。

メンバーへのポインター演算子の結果は、メンバーの型 (この場合は `char *`) になります。

次のコードでは、メンバーへのポインターを使用して、メンバー関数 `GetCaption` および `SetCaption` を呼び出します。

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>メンバーへのポインターに関する制約

静的メンバーのアドレスは、メンバーへのポインターではありません。 それは静的メンバーの 1 つのインスタンスへの通常のポインターです。 特定のクラスのすべてのオブジェクトに対して静的メンバーのインスタンスが1つだけ存在するので、通常のアドレスの ( **&** ) 演算子と逆参照演算子 (<strong>\*</strong>) を使用できます。

## <a name="pointers-to-members-and-virtual-functions"></a>メンバーと仮想関数へのポインター

メンバー関数へのポインターによる仮想関数の呼び出しは、関数が直接呼び出されているように機能します。v-table から正しい関数が検索され、呼び出されます。

この場合も、仮想関数が正しく機能するうえで重要なことは、基底クラスへのポインターを介して仮想関数を呼び出すことです。 (仮想関数の詳細については、「[仮想関数](../cpp/virtual-functions.md)」を参照してください)。

次のコードは、メンバー関数へのポインターを介して仮想関数を呼び出す方法を示しています。

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
    public:
    virtual void Print();
};
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

//Output: Print function for class Base
Print function for class Derived
```