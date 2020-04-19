---
title: this ポインター
description: this ポインターは、非静的メンバー関数内の現在のオブジェクトへのコンパイラによって生成されたポインターです。
ms.date: 01/22/2020
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- this
- class
- struct
- union
- sizeof
- const
- volatile
ms.openlocfilehash: 58bba2edd7a457c624b747b5a65d209995852848
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518336"
---
# <a name="opno-locthis-pointer"></a>this ポインター

**this** ポインターは、 **class** 、 **struct** 、または **union** 型の非静的メンバー関数内でのみアクセスできるポインターです。 これは、呼び出されるメンバー関数によって処理されるオブジェクトを指します。 静的メンバー関数には **this** ポインターがありません。

## <a name="syntax"></a>構文

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>Remarks

オブジェクトの **this** ポインターは、オブジェクト自体の一部ではありません。 オブジェクトの **sizeof** ステートメントの結果には反映されません。 オブジェクトに対して非静的メンバー関数が呼び出されると、コンパイラは、オブジェクトのアドレスを非表示の引数として関数に渡します。 たとえば、次の関数を呼び出してみましょう。

```cpp
myDate.setMonth( 3 );
```

次のように解釈できます。

```cpp
setMonth( &myDate, 3 );
```

オブジェクトのアドレスは、メンバー関数内から **this** ポインターとして使用できます。 ほとんどの **this** ポインターは暗黙的に使用されます。 classのメンバーを参照するときに明示的な **this** を使用することは、必要ではありません。 例:

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

**this** ポインターは、自己参照を防ぐためにも使用されます。

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
> **this** ポインターは不変であるため、 **this** ポインターへの割り当ては許可されません。 thisへのC++許可された割り当ての以前の実装。

場合によっては、 **this** ポインターが直接使用されることがあります。たとえば、自己参照データ構造体を操作するために、現在のオブジェクトのアドレスが必要な場合です。

## <a name="example"></a>使用例

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

## <a name="type-of-the-opno-locthis-pointer"></a>this ポインターの型

**this** ポインターの型は、関数宣言内で **const** と **volatile** キーワードを使用して変更できます。 これらの属性のいずれかを持つ関数を宣言するには、関数の引数リストの後にキーワードを追加します。

例を考えてみましょう。

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

前のコードでは、 **this** ポインターが **const** オブジェクトへの **const** ポインターとして扱われるメンバー関数 `X`を宣言しています。 Cv-*リスト*オプションの組み合わせを使用できますが、ポインター自体ではなく、 **this** ポインターによってポイントされているオブジェクトは常に変更されます。 次の宣言は、関数 `X`を宣言しています。ここで、 **this** ポインターは **const** オブジェクトへの **const** ポインターです。

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

メンバー関数内の **this** の型は、次の構文によって記述されます。 *Cv 修飾子リスト*は、メンバー関数の宣言子から決定されます。 **const** または **volatile** (またはその両方) を指定できます。 *class-* classの名前を指定します。

[*cv-修飾子リスト*] *classの種類* **\* const this**

言い換えると、 **this** ポインターは常に const ポインターです。 再割り当てできません。  メンバー関数の宣言で使用される **const** または **volatile** 修飾子は、その関数のスコープ内の **this** ポインターが指す class インスタンスに適用されます。

次の表は、これらの修飾子の機能について詳細を示します。

### <a name="semantics-of-opno-locthis-modifiers"></a>this 修飾子のセマンティクス

|Modifier|説明|
|--------------|-------------|
|**const**|メンバーデータを変更できません。 **const** されていないメンバー関数を呼び出すことはできません。|
|**volatile**|メンバーデータは、アクセスされるたびにメモリから読み込まれます。特定の最適化を無効にします。|

**const** されていないメンバー関数に **const** オブジェクトを渡すと、エラーになります。

同様に、 **volatile** されていないメンバー関数に **volatile** オブジェクトを渡すことも、エラーになります。

**const** として宣言されたメンバー関数は、メンバーデータを変更できません。このような関数では、 **this** ポインターは **const** オブジェクトへのポインターです。

> [!NOTE]
> コンストラクターとデストラクターを **const** または **volatile** として宣言することはできません。 ただし、 **const** オブジェクトまたは **volatile** オブジェクトで呼び出すことができます。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)
