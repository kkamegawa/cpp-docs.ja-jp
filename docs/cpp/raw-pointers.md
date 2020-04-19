---
title: 生のポインターC++()
description: で生のポインターを使用する方法C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 9ea498c254bc37dc8dc550232127cb2db3bc0886
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250686"
---
# <a name="raw-pointers-c"></a>生のポインターC++()

ポインターは、オブジェクトのアドレスをメモリに格納し、そのオブジェクトにアクセスするために使用される変数の一種です。 *生のポインター*は、[スマートポインター](smart-pointers-modern-cpp.md)などのカプセル化されたオブジェクトによって有効期間が制御されないポインターです。 生のポインターには、別の非ポインター変数のアドレスを割り当てることも、 [nullptr](nullptr.md)の値を割り当てることもできます。 値が割り当てられていないポインターには、ランダムなデータが含まれています。

ポインターを*逆*参照して、そのポインターが指すオブジェクトの値を取得することもできます。 *メンバーアクセス演算子*は、オブジェクトのメンバーへのアクセスを提供します。

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

ポインターは、型指定されたオブジェクトを指すことも、 **void**にすることもできます。 プログラムは、メモリ内の[ヒープ](https://wikipedia.org/wiki/Heap)に新しいオブジェクトを割り当てると、そのオブジェクトのアドレスをポインターの形式で受け取ります。 このようなポインターは、所有している*ポインター*と呼ばれます。不要になったときにヒープ割り当てオブジェクトを明示的に削除するには、所有しているポインター (またはそのコピー) を使用する必要があります。 メモリの削除に失敗すると、*メモリリーク*が発生し、そのメモリの場所をコンピューター上の他のプログラムで使用できなくなります。 詳細については、「 [new および delete 演算子](new-and-delete-operators.md)」を参照してください。

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

ポインター ( **const**として宣言されていない場合) は、メモリ内の新しい位置を指すようにインクリメントまたはデクリメントできます。 これは*ポインター演算*と呼ばれ、配列またはその他のデータ構造内の要素を反復処理するために C スタイルのプログラミングで使用されます。 **Const**ポインターを別のメモリ位置を指すようにすることはできません。その意味は[参照](references-cpp.md)とよく似ています。 詳細については、「 [const および volatile ポインター](const-and-volatile-pointers.md)」を参照してください。

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c; 
    // pconst2 = &c2; // Error! pconst2 is const.
```

64ビットオペレーティングシステムでは、ポインターのサイズは64ビットです。システムのポインターサイズによって、使用可能なメモリの量が決まります。 ポインターのすべてのコピーが同じメモリ位置を指しています。 ポインター (および参照) は、オブジェクト全体をC++コピーするよりも、オブジェクトの64ビットアドレスをコピーする方がはるかに効率的なので、より大きなオブジェクトを関数との間でやり取りするために、で広く使用されています。 関数を定義する場合は、オブジェクトを変更する関数を使用する場合を除き、ポインターパラメーターを**const**として指定します。 一般に、オブジェクトの値が**nullptr**である可能性がある場合を除き、オブジェクトを関数に渡すには、 **const**参照を使用することをお勧めします。

[関数へのポインター](#pointers_to_functions)を使用すると、関数を他の関数に渡すことができ、C スタイルのプログラミングでは "コールバック" に使用されます。 モダンC++では、この目的に[ラムダ式](lambda-expressions-in-cpp.md)を使用します。

## <a name="initialization-and-member-access"></a>初期化とメンバーアクセス

次の例は、生のポインターを宣言し、ヒープに割り当てられたオブジェクトを使用して初期化する方法と、その使用方法を示しています。 また、生のポインターに関連するいくつかの危険についても示します。 (最近C++ではなく C スタイルのプログラミングであることに注意してください)。

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>ポインターの算術演算と配列

ポインターと配列は密接に関連しています。 配列が値渡しで関数に渡されると、最初の要素へのポインターとして渡されます。 次の例は、ポインターと配列の次の重要なプロパティを示しています。

- `sizeof` 演算子は、配列の合計サイズ (バイト単位) を返します。
- 要素の数を決定するには、合計バイトを1つの要素のサイズで除算します。
- 配列が関数に渡されると、 *decays*はポインター型になります。
- ポインターに適用されたときの `sizeof` 演算子は、ポインターのサイズ、x86 の場合は4バイト、x64 の場合は8バイトを返します。

```cpp
#include <iostream>

void func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

特定の算術演算を非定数ポインターに対して実行して、新しいメモリ位置を指すようにすることができます。 ポインターは、 **++** 、 **+=** 、 **-=** 、および **--** の各演算子を使用してインクリメントおよびデクリメントできます。 この手法は配列で使用でき、型指定されていないデータのバッファーで特に便利です。 **Void\*** **char** (1 バイト) のサイズによってインクリメントされます。 型指定されたポインターは、ポインターが指す型のサイズによってインクリメントされます。

次の例は、ポインター演算を使用して、Windows 上のビットマップ内の個々のピクセルにアクセスする方法を示しています。 **New**と**delete**、および逆参照演算子の使用に注意してください。 

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>void * ポインター

**Void**へのポインターは、単純に生のメモリ位置を指します。 場合によっては、コードと C 関数の間C++を渡すときなどに、 **void\*** ポインターを使用する必要があります。 

型指定されたポインターが void ポインターにキャストされた場合、メモリ位置の内容は変更されませんが、インクリメントまたはデクリメント操作を実行できないように、型情報は失われます。 たとえば、MyClass * から void * へのメモリ位置をキャストして、再び MyClass * に戻ることができます。 このような操作は本質的にエラーが発生しやすく、エラーを回避するために細心の注意が必要です。 最新C++では、絶対に必要な場合を除き、void ポインターを使用することはできません。

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    for(char* c = static_cast<char*>(pvoid); pvoid < &pvoid + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers_to_functions"></a>関数へのポインター

C スタイルのプログラミングでは、関数ポインターは主に他の関数に関数を渡すために使用されます。 このシナリオでは、呼び出し元は関数の動作を変更せずにカスタマイズできます。 最新C++の[ラムダ式](lambda-expressions-in-cpp.md)では、より高いタイプセーフとその他の利点により、同じ機能が提供されます。

関数ポインター宣言は、ポイント先の関数が持つ必要があるシグネチャを指定します。

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

次の例は、`std::string` を受け取り、`std::string`を返す関数をパラメーターとして受け取る関数 `combine` を示しています。 `combine` に渡される関数に応じて、文字列を先頭または末尾に追加します。

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>参照

[スマートポインター](smart-pointers-modern-cpp.md)
[間接演算子: *](indirection-operator-star.md)<br/>
[address-of 演算子: &](address-of-operator-amp.md)</br>
[に戻るC++](welcome-back-to-cpp-modern-cpp.md)
