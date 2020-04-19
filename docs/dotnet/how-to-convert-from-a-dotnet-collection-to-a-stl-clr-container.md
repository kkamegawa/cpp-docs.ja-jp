---
title: '方法: .NET コレクションを STL/CLR コンテナーに変換します。'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 836623f6d539b7b28765763a3dc36d477f8c1499
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387553"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>方法: .NET コレクションを STL/CLR コンテナーに変換します。

このトピックでは、同等の STL/CLR コンテナーを .NET コレクションに変換する方法を示します。 例として、.NET に変換する方法を説明します<xref:System.Collections.Generic.List%601>、STL/CLR に[ベクター](../dotnet/vector-stl-clr.md) .NET に変換する方法および<xref:System.Collections.Generic.Dictionary%602>、STL/CLR に[マップ](../dotnet/map-stl-clr.md)手順はすべてのコレクションとコンテナーに似ていますが、.

### <a name="to-create-a-container-from-a-collection"></a>コレクションから、コンテナーを作成するには

1. コレクション全体を変換するには、STL/CLR コンテナーを作成し、コレクションをコンス トラクターに渡します。

   最初の例では、この手順を示します。

または

1. 作成して汎用 STL/CLR コンテナーを作成、 [collection_adapter](../dotnet/collection-adapter-stl-clr.md)オブジェクト。 .NET コレクション インターフェイスは、このテンプレート クラスは、引数として受け取ります。 どのインターフェイスがサポートされていることを確認するには、次を参照してください。 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)します。

1. コンテナーを .NET コレクションの内容をコピーします。 これを行う、STL/CLR を使用して[アルゴリズム](../dotnet/algorithm-stl-clr.md)、またはによって .NET コレクションを反復処理して、各要素のコピーを STL/CLR コンテナーに挿入します。

   2 番目の例では、この手順を示します。

## <a name="example"></a>例

この例では、ジェネリック型を作成します<xref:System.Collections.Generic.List%601>を 5 つの要素を追加します。 次に、作成、`vector`を受け取るコンス トラクターを使用して、<xref:System.Collections.Generic.IEnumerable%601>を引数として。

```
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>例

この例では、ジェネリック型を作成します<xref:System.Collections.Generic.Dictionary%602>を 5 つの要素を追加します。 次に、作成、`collection_adapter`をラップする、<xref:System.Collections.Generic.Dictionary%602>単純な STL/CLR コンテナーとして。 最後に、作成、`map`の内容をコピーし、<xref:System.Collections.Generic.Dictionary%602>を`map`を反復処理して、`collection_adapter`します。 このプロセス中を使用して、新しいペアを作成、`make_pair`関数とに直接新しいペアを挿入、`map`します。

```
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>関連項目

[STL/CLR ライブラリ リファレンス](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[方法: STL/CLR コンテナーを .NET コレクションに変換する](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
