---
title: STL/CLR ライブラリ リファレンス
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: b3c25a40fdb5bade02e112b13d16420b248a177f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384635"
---
# <a name="stlclr-library-reference"></a>STL/CLR ライブラリ リファレンス

STL/CLR ライブラリでは、C++ と .NET Framework 共通言語ランタイム (CLR) で使用するため、C++ 標準ライブラリ コンテナーに似たインターフェイスを提供します。 STL/CLR は、C++ 標準ライブラリの Microsoft 実装から完全に分離します。 STL/CLR では、レガシ サポートのために維持されますが、C++ 標準の最新の状態が保持されません。 ネイティブの使用を強くお勧め[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)STL/CLR 可能な限りではなくコンテナー。

STL/CLR を使用するには

- ヘッダーが含まれる、 **cliext**通常に対応する C++ 標準ライブラリではなくサブディレクトリが含まれます。

- ライブラリ名は、`cliext::` ではなく `std::` で修飾します。

STL/CLR ライブラリは、C++ と .NET Framework 共通言語ランタイム (CLR) で使用するため、STL のようなインターフェイスを提供します。 このライブラリは、レガシ サポートのために維持されますが、C++ 標準の最新の状態が保持されません。 ネイティブの使用を強くお勧め[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)STL/CLR ではなくコンテナー。

## <a name="in-this-section"></a>このセクションの内容

[cliext 名前空間](../dotnet/cliext-namespace.md)<br/>
STL/CLR ライブラリのすべての型を含む名前空間について説明します。

[STL/CLR コンテナー](../dotnet/stl-clr-containers.md)<br/>
コンテナー要素を挿入できる要素の型と所有権の問題の要件など、C++ 標準ライブラリ内にあるコンテナーの概要を示します。

[STL/CLR コンテナー要素の要件](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
C++ 標準ライブラリ コンテナーに挿入されたすべての参照型の最小要件について説明します。

[方法: .NET コレクションを STL/CLR コンテナーに変換する](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
.NET コレクションを STL/CLR コンテナーに変換する方法について説明します。

[方法: STL/CLR コンテナーを .NET コレクションに変換する](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
STL/CLR コンテナーを .NET コレクションに変換する方法について説明します。

[方法: アセンブリから STL/CLR コンテナーを公開する](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
C++ アセンブリで記述された複数の STL/CLR コンテナー要素を表示する方法を示します。

また、このセクションでは STL/CLR の次のコンポーネントについても説明します。

|||
|-|-|
|[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)|
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[for each、in](../dotnet/for-each-in.md)|
|[functional (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)|
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[list (STL/CLR)](../dotnet/list-stl-clr.md)|
|[map (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)|
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[queue (STL/CLR)](../dotnet/queue-stl-clr.md)|
|[set (STL/CLR)](../dotnet/set-stl-clr.md)|[stack (STL/CLR)](../dotnet/stack-stl-clr.md)|
|[utility (STL/CLR)](../dotnet/utility-stl-clr.md)|[vector (STL/CLR)](../dotnet/vector-stl-clr.md)|

## <a name="see-also"></a>関連項目

[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
