---
title: '方法: STL/CLR コンテナーから .NET コレクションに変換します。'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: cf67e362751dd164916cc94cd644d55110d88a5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387527"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>方法: STL/CLR コンテナーから .NET コレクションに変換します。

このトピックでは、同等の .NET のコレクションを STL/CLR コンテナーに変換する方法を示します。 例として、STL/CLR を変換する方法を説明します[ベクター](../dotnet/vector-stl-clr.md) .net <xref:System.Collections.Generic.ICollection%601> 、STL/CLR を変換する方法および[マップ](../dotnet/map-stl-clr.md).net<xref:System.Collections.Generic.IDictionary%602>プロシージャはすべてのコレクションと似ていますとコンテナー。

### <a name="to-create-a-collection-from-a-container"></a>コンテナーからコレクションを作成するには

1. 次の方法のいずれかを使用します。

   - コンテナーの一部を変換するには、呼び出し、 [make_collection](../dotnet/make-collection-stl-clr.md)関数、および .NET コレクションにコピーするには、begin の反復子と STL/CLR コンテナーの末尾の反復子を渡します。 STL/CLR の反復子は、このテンプレート関数は、テンプレート引数として受け取ります。 最初の例では、この方法を示します。

   - コンテナー全体を変換するには、適切な .NET コレクション インターフェイスまたはインターフェイスのコレクションにコンテナーをキャストします。 2 番目の例では、この方法を示します。

## <a name="example"></a>例

この例で、STL/CLR を作成します`vector`を 5 つの要素を追加します。 呼び出すことによって .NET コレクションを作成し、`make_collection`関数。 最後に、新しく作成されたコレクションの内容を表示します。

```
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

## <a name="example"></a>例

この例で、STL/CLR を作成します`map`を 5 つの要素を追加します。 .NET を作成し、<xref:System.Collections.Generic.IDictionary%602>を割り当てると、`map`直接にします。 最後に、新しく作成されたコレクションの内容を表示します。

```
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>関連項目

[STL/CLR ライブラリ リファレンス](../dotnet/stl-clr-library-reference.md)<br/>
[方法: .NET コレクションを STL/CLR コンテナーに変換する](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
