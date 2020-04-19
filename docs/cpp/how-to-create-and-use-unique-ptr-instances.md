---
title: '方法: unique_ptr インスタンスを作成して使用する'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 4b3362f71d1ccab0efb03d7e8705c6b3f25f9780
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246525"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>方法: unique_ptr インスタンスを作成して使用する

[Unique_ptr](../standard-library/unique-ptr-class.md)はそのポインターを共有しません。 別の `unique_ptr`にコピーしたり、関数に値で渡したりすることはできませC++ん。また、コピーを作成する必要がある標準ライブラリアルゴリズムで使用することもできません。 `unique_ptr` ができるのは移動だけです。 この場合、メモリ リソースの所有権は別の `unique_ptr` に移動し、元の `unique_ptr` はそれ以降、所有権を失います。 複数の所有者がオブジェクトを所有するとプログラム ロジックが複雑になるため、所有者を 1 人に制限することをお勧めします。 したがって、プレーンC++オブジェクト用のスマートポインターが必要な場合は、`unique_ptr`を使用し、`unique_ptr`を構築するときに[make_unique](../standard-library/memory-functions.md#make_unique)ヘルパー関数を使用します。

次の図では、2 つの `unique_ptr` のインスタンス間での所有権の移転を示します。

![一意&#95;の ptr の所有権の移動](media/unique_ptr.png "一意&#95;の ptr の所有権の移動")

`unique_ptr` は、 C++標準ライブラリの `<memory>` ヘッダーで定義されています。 これは生のポインターと同じように効率的であり、標準C++ライブラリのコンテナーで使用できます。 標準ライブラリコンテナーへC++の `unique_ptr` インスタンスの追加は効率的です。これは、`unique_ptr` の移動コンストラクターによってコピー操作が不要になるためです。

## <a name="example-1"></a>例 1

次の例では、`unique_ptr` インスタンスを作成し、関数間で渡す方法を示します。

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

これらの例は、`unique_ptr` の基本的な機能として、移動はできるが、コピーはできないことを示しています。 「移動」は `unique_ptr` に所有権を移転し、元の `unique_ptr` をリセットします。

## <a name="example-2"></a>例 2

次の例では、`unique_ptr` インスタンスを作成し、ベクター内で使用する方法を示します。

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

ループの範囲で、`unique_ptr` が参照によって渡されることに注意してください。 ここで値によって渡そうとすると、`unique_ptr` コピー コンストラクターが削除されるため、コンパイラによってエラーがスローされます。

## <a name="example-3"></a>例 3

次の例では、クラス メンバーである `unique_ptr` を初期化する方法を示しています。

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>例 4

[Make_unique](../standard-library/memory-functions.md#make_unique)を使用して配列への `unique_ptr` を作成することはできますが、`make_unique` を使用して配列要素を初期化することはできません。

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

その他の例については、「 [make_unique](../standard-library/memory-functions.md#make_unique)」を参照してください。

## <a name="see-also"></a>参照

[スマート ポインター (Modern C++)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
