---
title: this ポインター
ms.date: 11/04/2016
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
ms.openlocfilehash: c90a843ba978a98c1c61d9e096d62b85256ab0c4
ms.sourcegitcommit: d441305fb19131afbd7fc259d8cda63ea26f2343
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678328"
---
# <a name="this-pointer"></a>this ポインター

**この**ポインターは、ポインターの非静的メンバー関数内でのみアクセス可能な**クラス**、**構造体**、または**共用体**型。 これは、呼び出されるメンバー関数によって処理されるオブジェクトを指します。 静的メンバー関数はありません、**この**ポインター。

## <a name="syntax"></a>構文

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>Remarks

オブジェクトの**この**ポインター オブジェクト自体の一部でないの結果には反映されず、 **sizeof**オブジェクトのステートメント。 その代わりに、非静的メンバー関数がオブジェクトに対して呼び出されると、オブジェクトのアドレスが関数の隠し引数としてコンパイラに渡されます。 たとえば、次の関数を呼び出してみましょう。

```cpp
myDate.setMonth( 3 );
```

これは次のように解釈できます。

```cpp
setMonth( &myDate, 3 );
```

オブジェクトのアドレスは、メンバー関数内から利用できる、**この**ポインター。 ほとんどの用途**この**が暗黙的に指定します。 明示的に使用する、不要な場合は法律、**この**クラスのメンバーを参照する場合。 例えば:

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

式 `*this` は、通常、メンバー関数から現在のオブジェクトを返すために使用されます。

```cpp
return *this;
```

**この**ポインターは自己参照からの保護にも使用されます。

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
>  **この**ポインターは変更できない場合は、割り当てを**これ**は許可されていません。 C++ の初期の実装への割り当てを許可する**この**します。

場合によっては、**この**ポインターを直接使用 — たとえば、自己参照データを操作する構造体の現在のオブジェクトのアドレスが必要な場合。

## <a name="example"></a>例

```cpp
// this_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

class Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( const Buf & );
    void Display() { cout << buffer << endl; }

private:
    char*   buffer;
    size_t  sizeOfBuffer;
};

Buf::Buf( char* szBuffer, size_t sizeOfBuffer )
{
    sizeOfBuffer++; // account for a NULL terminator

    buffer = new char[ sizeOfBuffer ];
    if (buffer)
    {
        strcpy_s( buffer, sizeOfBuffer, szBuffer );
        sizeOfBuffer = sizeOfBuffer;
    }
}

Buf& Buf::operator=( const Buf &otherbuf )
{
    if( &otherbuf != this )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *this;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-this-pointer"></a>this ポインターの型

**この**ポインターの型は、関数宣言で変更できる、 **const**と**揮発性**キーワード。 これらのキーワードの属性を持つものとして関数を宣言するには、関数の引数リストの後にキーワードを追加します。

次の例について考えます。

```cpp
// type_of_this_pointer1.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

上記のコードは、メンバー関数を宣言します`X`、これで、**これ**ポインターとして扱われます、 **const**へのポインターを**const**オブジェクト。 組み合わせ*リスト mod cv ・* オプションを使用できますしますが、指すオブジェクトを常に変更**この**ではなく、**この**ポインター自体。 そのため、次の宣言は関数を宣言します。 `X`、**この**ポインターが、 **const**へのポインターを**const**オブジェクト。

```cpp
// type_of_this_pointer2.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

型**この**次の構文で、メンバー関数が説明されている場所*cv 修飾子のリスト*はメンバー関数宣言子から決定され、 **const**または**揮発性**(または両方) および*クラス型*クラスの名前を指定します。

*[cv 修飾子一覧] クラス型* **&#42; const これ**

つまり、**この**; の const ポインターは、常に再割り当てできません。  **Const**または**揮発性**メンバー関数の宣言で使用される修飾子が指すクラス インスタンスに適用**この**でその関数のスコープ。

次の表は、これらの修飾子の機能について詳細を示します。

### <a name="semantics-of-this-modifiers"></a>this の修飾子のセマンティクス

|修飾子|説明|
|--------------|-------------|
|**const**|メンバーのデータを変更することはできません。ないメンバー関数を呼び出すことはできません**const**します。|
|**volatile**|メンバー データはアクセスされるたびにメモリから読み込まれます。特定の最適化は無効になります。|

渡すとエラーには、 **const**オブジェクトでないメンバー関数を**const**します。 同様に、渡すとエラーには、**揮発性**オブジェクトでないメンバー関数を**揮発性**します。

メンバー関数として宣言**const**メンバー データを変更することはできません: このような関数の場合、**この**ポインターへのポインターを**const**オブジェクト。

> [!NOTE]
>  コンス トラクターとデストラクターとして宣言することはできません**const**または**揮発性**します。 あること、ただしで呼び出される**const**または**揮発性**オブジェクト。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)