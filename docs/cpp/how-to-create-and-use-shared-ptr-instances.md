---
title: '方法: shared_ptr インスタンスを作成して使用する'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: 9820e4cd2d1b981d82760fc1cea4e07c85792177
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245827"
---
# <a name="how-to-create-and-use-shared_ptr-instances"></a>方法: shared_ptr インスタンスを作成して使用する

`shared_ptr` 型は、C++ 標準ライブラリ内のスマート ポインターであり、複数の所有者がメモリ内のオブジェクトの有効期間を管理する必要が生じる可能性があるシナリオを想定して設計されたものです。 `shared_ptr` を初期化した後、そのポインターをコピーすること、関数の引数内の値として渡すこと、および他の `shared_ptr` インスタンスに割り当てることができます。 すべてのインスタンスは同じオブジェクトを指し、1 つの "コントロール ブロック" へのアクセスを共有します。このコントロール ブロックは、新しい `shared_ptr` が追加されるとき、スコープ外になるとき、またはリセットされるときに必ず参照カウントをインクリメントおよびデクリメントします。 参照カウントが 0 に達したときに、コントロール ブロックはメモリ リソースと自らを削除します。

次の図に、1 つのメモリ位置を指す `shared_ptr` の複数のインスタンスを示します。

![共有ポインターの図](media/shared_ptr.png "共有ポインターの図")

## <a name="example-setup"></a>設定例

この後の例はここで示された必要なヘッダーをすべて含み、必要な型をすべて宣言していることを前提としています。

```cpp
// shared_ptr-examples.cpp
// The following examples assume these declarations:
#include <algorithm>
#include <iostream>
#include <memory>
#include <string>
#include <vector>

struct MediaAsset
{
    virtual ~MediaAsset() = default; // make it polymorphic
};

struct Song : public MediaAsset
{
    std::wstring artist;
    std::wstring title;
    Song(const std::wstring& artist_, const std::wstring& title_) :
        artist{ artist_ }, title{ title_ } {}
};

struct Photo : public MediaAsset
{
    std::wstring date;
    std::wstring location;
    std::wstring subject;
    Photo(
        const std::wstring& date_,
        const std::wstring& location_,
        const std::wstring& subject_) :
        date{ date_ }, location{ location_ }, subject{ subject_ } {}
};

using namespace std;

int main()
{
    // The examples go here, in order:
    // Example 1
    // Example 2
    // Example 3
    // Example 4
    // Example 6
}
```

## <a name="example-1"></a>例 1

最初にメモリ リソースを作成するときは、可能な限り、[ を作成するために ](../standard-library/memory-functions.md#make_shared)make_shared`shared_ptr` 関数を使用してください。 `make_shared` は例外セーフです。 これは、コントロール ブロックとリソースにメモリを割り当てるために同じ呼び出しを使用し、その結果、構造のオーバーヘッドが削減されます。 `make_shared` を使用しない場合は、オブジェクトを `new` コンストラクターに渡す前にオブジェクトを作成するために、明示的な `shared_ptr` 式を使用する必要があります。 次の例では、新しいオブジェクトと共に `shared_ptr` を宣言して初期化するさまざまな方法を示します。

[!code-cpp[stl_smart_pointers#1](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>例 2

次の例では、別の `shared_ptr`によって既に割り当てられているオブジェクトの共有所有権を取得する `shared_ptr` インスタンスを宣言して初期化する方法を示します。 `sp2` が初期化された `shared_ptr`であることを想定します。

[!code-cpp[stl_smart_pointers#2](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>例 3

`shared_ptr` は、要素をコピーするアルゴリズムを使用しているときに、C++ の標準ライブラリ コンテナー内でも役立ちます。 基になるメモリが、必要とされている間は有効であり、必要なくなった後は無効になることを理解している場合は、要素を `shared_ptr` 内でラップし、他のコンテナーにコピーすることができます。 次の例では、ベクター内の `remove_copy_if` インスタンスに対して `shared_ptr` アルゴリズムを使用する方法を示します。

[!code-cpp[stl_smart_pointers#4](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>例 4

`dynamic_pointer_cast`, `static_pointer_cast` および `const_pointer_cast` を使用して、`shared_ptr` をキャストすることができます。 これらの関数は、`dynamic_cast`、`static_cast`、および `const_cast` の各演算子に似ています。 次の例では、基底クラスの `shared_ptr` のベクター内にある各要素の派生型をテストし、要素をコピーし、それらに関する情報を表示する方法を示します。

[!code-cpp[stl_smart_pointers#5](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>例 5

次の方法で、`shared_ptr` を別の関数に渡すことができます。

- 値渡しで `shared_ptr` を渡します。 これは、コピー コンストラクターを呼び出し、参照カウントをインクリメントし、呼び出し先を所有者にします。 この操作には小規模なオーバーヘッドがあり、渡そうとする `shared_ptr` オブジェクトの数によっては、非常に大規模になる可能性があります。 呼び出し元と呼び出し先の間にあるコード コントラクト (暗黙的または明示的) が、呼び出し先を所有者にすることを要求する場合は、このオプションを使用します。

- 参照または定数参照により、`shared_ptr` を渡します。 この場合、参照カウントはインクリメントされず、呼び出し元がスコープ内にとどまっている限り、呼び出し先はポインターにアクセスできます。 または、呼び出し先は参照に基づいて `shared_ptr` を作成し、その後、共有所有者になる方針を使用することもできます。 呼び出し元が呼び出し先を把握していない場合や、`shared_ptr` を渡す必要があり、パフォーマンス上の理由でコピー操作を回避したいと考える場合は、このオプションを使用します。

- 基になるポインター、または基になるオブジェクトへの参照を渡します。 この結果、呼び出し先はオブジェクトを使用できますが、そのオブジェクトを有効にして所有権を共有することや、有効期間を延長することはできません。 呼び出し先が、生ポインターから `shared_ptr` を作成する場合は、新しい `shared_ptr` は元のポインターから独立し、基になるリソースを制御することはできません。 呼び出し元と呼び出し先の間のコントラクトが、呼び出し元が `shared_ptr` の有効期間の所有権を保持することを明示的に指定する場合は、このオプションを使用します。

- `shared_ptr` を渡す方法を決定するときに、呼び出し先が、基になるリソースの所有権を共有する必要があるかどうかを判断してください。 "所有者" とは、基になるリソースを自らが必要とする限り、そのリソースを維持することができるオブジェクトまたは関数です。 呼び出し先が、(関数の) 有効期間を上回ってポインターの有効期間を延長できるようにすることを、呼び出し元が保証する必要がある場合は、最初のオプションを使用します。 呼び出し先が有効期間を延長するかどうかが問題にならない場合は、参照渡しを使用し、コピーするかどうかを呼び出し先に任せます。

- 基になるポインターへのアクセスをヘルパー関数に付与する必要があり、ヘルパー関数がそのポインターを使用するだけであり、呼び出し元関数が制御を返す前にヘルパー関数が制御を返すことがわかっている場合は、関数は基になるポインターの所有権を共有する必要はありません。 ヘルパー関数は、呼び出し元の `shared_ptr` の有効期間内にのみ、ポインターにアクセスする必要があります。 この場合は、`shared_ptr` を参照渡しにするか、生ポインターを渡すか、基になるオブジェクトへの参照を渡す方法が安全です。 この方法で渡すと、パフォーマンスに関するある程度の利点が生じ、プログラミングの意図を示すのに役立つ可能性もあります。

- 時には、たとえば `std::vector<shared_ptr<T>>` のように、各 `shared_ptr` をラムダ式の本体または名前付き関数オブジェクトに渡す必要が生じることがあります。 ラムダまたは関数がそのポインターを格納しない場合は、`shared_ptr` の参照渡しを行い、各要素に対してコピー コンストラクターが呼び出されることを防止します。

## <a name="example-6"></a>例 6

`shared_ptr` インスタンスによって所有されているメモリ上のポインター比較を有効にするために、`shared_ptr` がさまざまな比較演算子をオーバーロードする方法を次の例に示します。

[!code-cpp[stl_smart_pointers#3](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>参照

[スマート ポインター (Modern C++)](smart-pointers-modern-cpp.md)
