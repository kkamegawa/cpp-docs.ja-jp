---
title: '方法: アセンブリから STL/CLR コンテナーを公開します。'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
ms.openlocfilehash: 206a95cbaa808f54d7ae0e500b5a2bea272d974b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387332"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>方法: アセンブリから STL/CLR コンテナーを公開します。

などの STL/CLR コンテナー`list`と`map`テンプレート ref クラスとして実装されます。 C++ テンプレートは、コンパイル時にインスタンス化ため正確に同じシグネチャが異なるアセンブリにある 2 つのテンプレート クラスは実際にはさまざまな種類にします。 つまり、アセンブリ境界を越えてテンプレート クラスを使用することはできません。

STL/CLR コンテナーがジェネリック インターフェイスを実装するのには、アセンブリ間で共有可能な<xref:System.Collections.Generic.ICollection%601>します。 このジェネリック インターフェイスを使用すると、STL/CLR コンテナーを含む C++、c#、および Visual Basic の場合は、ジェネリックをサポートするすべての言語にアクセスできます。

このトピックでは、という名前の C++ アセンブリで記述された複数の STL/CLR コンテナーの要素を表示する方法を示します`StlClrClassLibrary`します。 2 つのアセンブリへのアクセスに紹介`StlClrClassLibrary`します。 最初のアセンブリは、C++、および c# では、2 つ目で記述されます。

使用してコンテナーのジェネリック インターフェイスをアクセスすることができる場合、両方のアセンブリは C++ で記述された、その`generic_container`typedef。 たとえば、次の種類のコンテナーがある`cliext::vector<int>`、そのジェネリック インターフェイスは: `cliext::vector<int>::generic_container`。 使用して、ジェネリック インターフェイス経由で、反復子を取得する同様に、`generic_iterator`に示すように、typedef:`cliext::vector<int>::generic_iterator`します。

C++ ヘッダー ファイルでは、これらの typedef が宣言されている、ために、他の言語で記述されたアセンブリは、それらを使用できません。 そのため、ジェネリック インターフェイスにアクセスする`cliext::vector<int>`(C#) またはその他の .NET 言語で使用`System.Collections.Generic.ICollection<int>`します。 このコレクションを反復処理に使用して、`foreach`ループします。

次の表では、各 STL/CLR コンテナーを実装するジェネリック インターフェイスを示します。

|STL/CLR コンテナー|ジェネリック インターフェイス|
|------------------------|-----------------------|
|`deque<T>`|`ICollection<T>`|
|`hash_map<K, V>`|`IDictionary<K, V>`|
|`hash_multimap<K, V>`|`IDictionary<K, V>`|
|`hash_multiset<T>`|`ICollection<T>`|
|`hash_set<T>`|`ICollection<T>`|
|`list<T>`|`ICollection<T>`|
|`map<K, V>`|`IDictionary<K, V>`|
|`multimap<K, V>`|`IDictionary<K, V>`|
|`multiset<T>`|`ICollection<T>`|
|`set<T>`|`ICollection<T>`|
|`vector<T>`|`ICollection<T>`|

> [!NOTE]
> `queue`、 `priority_queue`、および`stack`ジェネリック インターフェイスを実装しないと、アセンブリ間のアクセスをすることはできませんが、コンテナーは反復子をサポートしていません。

## <a name="example-1"></a>例 1

### <a name="description"></a>説明

この例では、プライベートの STL/CLR メンバー データを格納する C++ クラスを宣言します。 クラスのプライベート コレクションへのアクセスを許可するパブリック メソッドを宣言します。 2 つの方法で、C++ のクライアントのいずれかおよびその他の .NET クライアントのいずれかを行います。

### <a name="code"></a>コード

```cpp
// StlClrClassLibrary.h
#pragma once

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/stack>
#include <cliext/vector>

using namespace System;
using namespace System::Collections::Generic;
using namespace cliext;

namespace StlClrClassLibrary {

    public ref class StlClrClass
    {
    public:
        StlClrClass();

        // These methods can be called by a C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        deque<wchar_t>::generic_container ^GetDequeCpp();
        list<float>::generic_container ^GetListCpp();
        map<int, String ^>::generic_container ^GetMapCpp();
        set<double>::generic_container ^GetSetCpp();
        vector<int>::generic_container ^GetVectorCpp();

        // These methods can be called by a non-C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        ICollection<wchar_t> ^GetDequeCs();
        ICollection<float> ^GetListCs();
        IDictionary<int, String ^> ^GetMapCs();
        ICollection<double> ^GetSetCs();
        ICollection<int> ^GetVectorCs();

    private:
        deque<wchar_t> ^aDeque;
        list<float> ^aList;
        map<int, String ^> ^aMap;
        set<double> ^aSet;
        vector<int> ^aVector;
    };
}
```

## <a name="example-2"></a>例 2

### <a name="description"></a>説明

この例では、例 1 で宣言されたクラスを実装します。 マニフェスト ツールを使用してクライアントがこのクラス ライブラリを使用するためには、 **mt.exe** DLL にマニフェスト ファイルを埋め込む。 詳細については、コードのコメントを参照してください。

マニフェスト ツールとサイド バイ サイド アセンブリの詳細については、次を参照してください。 [c/c++ 分離アプリケーションの構築とサイド バイ サイド アセンブリ](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)します。

### <a name="code"></a>コード

```cpp
// StlClrClassLibrary.cpp
// compile with: /clr /LD /link /manifest
// post-build command: (attrib -r StlClrClassLibrary.dll & mt /manifest StlClrClassLibrary.dll.manifest /outputresource:StlClrClassLibrary.dll;#2 & attrib +r StlClrClassLibrary.dll)

#include "StlClrClassLibrary.h"

namespace StlClrClassLibrary
{
    StlClrClass::StlClrClass()
    {
        aDeque = gcnew deque<wchar_t>();
        aDeque->push_back(L'a');
        aDeque->push_back(L'b');

        aList = gcnew list<float>();
        aList->push_back(3.14159f);
        aList->push_back(2.71828f);

        aMap = gcnew map<int, String ^>();
        aMap[0] = "Hello";
        aMap[1] = "World";

        aSet = gcnew set<double>();
        aSet->insert(3.14159);
        aSet->insert(2.71828);

        aVector = gcnew vector<int>();
        aVector->push_back(10);
        aVector->push_back(20);
    }

    deque<wchar_t>::generic_container ^StlClrClass::GetDequeCpp()
    {
        return aDeque;
    }

    list<float>::generic_container ^StlClrClass::GetListCpp()
    {
        return aList;
    }

    map<int, String ^>::generic_container ^StlClrClass::GetMapCpp()
    {
        return aMap;
    }

    set<double>::generic_container ^StlClrClass::GetSetCpp()
    {
        return aSet;
    }

    vector<int>::generic_container ^StlClrClass::GetVectorCpp()
    {
        return aVector;
    }

    ICollection<wchar_t> ^StlClrClass::GetDequeCs()
    {
        return aDeque;
    }

    ICollection<float> ^StlClrClass::GetListCs()
    {
        return aList;
    }

    IDictionary<int, String ^> ^StlClrClass::GetMapCs()
    {
        return aMap;
    }

    ICollection<double> ^StlClrClass::GetSetCs()
    {
        return aSet;
    }

    ICollection<int> ^StlClrClass::GetVectorCs()
    {
        return aVector;
    }
}
```

## <a name="example-3"></a>例 3

### <a name="description"></a>説明

この例では、例 1 および 2 で作成したクラス ライブラリを使用する C++ クライアントを作成します。 このクライアントを使用して、`generic_container`コンテナーを反復処理して、その内容を表示する STL/CLR コンテナーの typedef。

### <a name="code"></a>コード

```cpp
// CppConsoleApp.cpp
// compile with: /clr /FUStlClrClassLibrary.dll

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/vector>

using namespace System;
using namespace StlClrClassLibrary;
using namespace cliext;

int main(array<System::String ^> ^args)
{
    StlClrClass theClass;

    Console::WriteLine("cliext::deque contents:");
    deque<wchar_t>::generic_container ^aDeque = theClass.GetDequeCpp();
    for each (wchar_t wc in aDeque)
    {
        Console::WriteLine(wc);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::list contents:");
    list<float>::generic_container ^aList = theClass.GetListCpp();
    for each (float f in aList)
    {
        Console::WriteLine(f);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::map contents:");
    map<int, String ^>::generic_container ^aMap = theClass.GetMapCpp();
    for each (map<int, String ^>::value_type rp in aMap)
    {
        Console::WriteLine("{0} {1}", rp->first, rp->second);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::set contents:");
    set<double>::generic_container ^aSet = theClass.GetSetCpp();
    for each (double d in aSet)
    {
        Console::WriteLine(d);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::vector contents:");
    vector<int>::generic_container ^aVector = theClass.GetVectorCpp();
    for each (int i in aVector)
    {
        Console::WriteLine(i);
    }
    Console::WriteLine();

    return 0;
}
```

### <a name="output"></a>出力

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="example-4"></a>例 4

### <a name="description"></a>説明

この例では、例 1 および 2 で作成したクラス ライブラリを使用する c# クライアントを作成します。 このクライアントを使用して、 <xref:System.Collections.Generic.ICollection%601> STL/CLR コンテナー、コンテナーを反復処理して、その内容を表示する方法。

### <a name="code"></a>コード

```csharp
// CsConsoleApp.cs
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll

using System;
using System.Collections.Generic;
using StlClrClassLibrary;
using cliext;

namespace CsConsoleApp
{
    class Program
    {
        static int Main(string[] args)
        {
            StlClrClass theClass = new StlClrClass();

            Console.WriteLine("cliext::deque contents:");
            ICollection<char> iCollChar = theClass.GetDequeCs();
            foreach (char c in iCollChar)
            {
                Console.WriteLine(c);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::list contents:");
            ICollection<float> iCollFloat = theClass.GetListCs();
            foreach (float f in iCollFloat)
            {
                Console.WriteLine(f);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::map contents:");
            IDictionary<int, string> iDict = theClass.GetMapCs();
            foreach (KeyValuePair<int, string> kvp in iDict)
            {
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::set contents:");
            ICollection<double> iCollDouble = theClass.GetSetCs();
            foreach (double d in iCollDouble)
            {
                Console.WriteLine(d);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::vector contents:");
            ICollection<int> iCollInt = theClass.GetVectorCs();
            foreach (int i in iCollInt)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            return 0;
        }
    }
}
```

### <a name="output"></a>出力

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="see-also"></a>関連項目

[STL/CLR ライブラリ リファレンス](../dotnet/stl-clr-library-reference.md)
