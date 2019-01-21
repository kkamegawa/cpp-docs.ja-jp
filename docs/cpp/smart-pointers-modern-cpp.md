---
title: スマート ポインター (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: c976f9ec72929f2c8ff91fb9f9594d91c7457365
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220661"
---
# <a name="smart-pointers-modern-c"></a>スマート ポインター (Modern C++)

標準ライブラリに含まれる最新の C++ プログラミングで*スマート ポインター*メモリの空きプログラムを確実に使用されますが、およびリソースのリークし例外セーフです。

## <a name="uses-for-smart-pointers"></a>スマート ポインターの使用

スマート ポインターがで定義されている、`std`で名前空間、 [\<メモリ >](../standard-library/memory.md)ヘッダー ファイル。 非常に重要ですが、 [RAII](../cpp/objects-own-resources-raii.md)または*Resource Acquisition Is Initialization*プログラミングのイディオムです。 この表現方法の主な目的は、オブジェクトのすべてのリソースが 1 行のコードで作成されて準備が完了するように、リソースの取得がオブジェクトの初期化と同時に行われるようにすることです。 具体的には、RAII の主要な原則は、ヒープ割り当てリソース (動的に割り当てられたメモリやシステム オブジェクト ハンドルなど) の所有権を、リソースを削除または解放するコードと関連するクリーンアップ コードがデストラクターに含まれるスタック割り当てオブジェクトに付与するというものです。

ほとんどの場合、生のポインターまたはリソース ハンドルを初期化して実際のリソースをポイントするとき、ポインターをすぐにスマート ポインターに渡します。 最新の C++ では、生のポインターは、パフォーマンスが重要な意味を持ち、所有権に関する混乱が発生する可能性がない限られたスコープ、ループ、またはヘルパー関数の小さなコード ブロックでのみ使用されます。

次の例では、生のポインターの宣言とスマート ポインターの宣言を比較します。

[!code-cpp[smart_pointers_intro#1](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

この例に示されているように、スマート ポインターは、スタック上で宣言し、ヒープ割り当てオブジェクトをポイントする生のポインターを使用して初期化するクラス テンプレートです。 スマート ポインターは、初期化後、生のポインターを所有します。 つまり、スマート ポインターは、生のポインターが指定するメモリの削除を担当します。 スマート ポインターのデストラクターには、削除する呼び出しが含まれています。スマート ポインターはスタック上で宣言されるため、スタックの別の場所で例外がスローされた場合でも、スマート ポインターがスコープ外に移動するとデストラクターが呼び出されます。

カプセル化されたポインターには、使い慣れたポインター演算子 `->` および `*` を使用することでアクセスします。これらの演算子には、カプセル化された生のポインターを返すためにスマート ポインター クラスがオーバーロードします。

C++ のスマート ポインターの表現方法は、C# などの言語でのオブジェクト作成に似ています。オブジェクトを作成し、システムが正しい時刻にファイルの削除を実行するようにします。 違いは、別個のガベージ コレクターがバックグラウンドで実行されないことです。メモリは、標準 C++ のスコープ規則を通じて管理されるため、ランタイム環境が高速かつ効率的になります。

> [!IMPORTANT]
>  特定のパラメーター リストの割り当て規則が原因でわずかなリソース リークが発生しないように、スマート ポインターは必ずパラメーター リストではなく別個のコード行に作成してください。

次の例はどのように、 `unique_ptr` C++ 標準ライブラリのスマート ポインター型は、ラージ オブジェクトへのポインターをカプセル化される可能性があります。

[!code-cpp[smart_pointers_intro#2](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

この例は、スマート ポインターを使用するために必要な次の手順を示しています。

1. 自動 (ローカル) 変数としてスマート ポインターを宣言します  (使用しないでください、**新しい**または`malloc`スマート ポインター自体の式です)。

1. 型パラメーターで、カプセル化されたポインターの pointed-to 型を指定します。

1. 生のポインターを渡す、**新しい**-スマート ポインター コンス トラクターで ed オブジェクト。 (これは、一部のユーティリティ関数またはスマート ポインター コンストラクターによって行われます)。

1. オーバーロードされた `->` および `*` 演算子を使用してオブジェクトにアクセスします。

1. スマート ポインターがオブジェクトを削除するようにします。

スマート ポインターは、メモリとパフォーマンスの両方の点でできる限り効率が高くなるように設計されています。 たとえば、`unique_ptr` の唯一のデータ メンバーはカプセル化されたポインターです。 これは、`unique_ptr` がそのポインターとまったく同じサイズ (4 バイトまたは 8 バイト) であることを意味します。 スマート ポインターによってオーバーロードされた * および -> 演算子を使用することでカプセル化されたポインターにアクセスしても、生のポインターに直接アクセスするよりそれほど遅くなるわけではありません。

スマート ポインターには、"ドット" 表記を使用してアクセスできる独自のメンバー関数があります。 たとえば、いくつかの C++ 標準ライブラリのスマート ポインターでは、ポインターの所有権を解放するリセット メンバー関数があります。 これは、次の例に示すように、スマート ポインターがスコープ外に移動する前に、スマート ポインターが所有するメモリを解放する場合に便利です。

[!code-cpp[smart_pointers_intro#3](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

スマート ポインターには、通常、生のポインターに直接アクセスする方法が用意されています。 C++ 標準ライブラリのスマート ポインターが、`get`メンバー関数は、この目的および`CComPtr`がパブリック`p`クラスのメンバー。 基になるポインターへの直接アクセスを用意することにより、スマート ポインターを使用して独自のコード内のメモリを管理し、スマート ポインターをサポートしないコードに生のポインターを渡すこともできます。

[!code-cpp[smart_pointers_intro#4](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>スマート ポインターの種類

次のセクションでは、Windows プログラミング環境で使用できるさまざまな種類のスマート ポインターの概要を示し、使用するタイミングについて説明します。

### <a name="c-standard-library-smart-pointers"></a>C++ 標準ライブラリのスマート ポインター

これらのスマート ポインターは、Plain Old C++ Object (POCO) にポインターをカプセル化する最初のオプションとして使用します。

- `unique_ptr`<br/>
   基になるポインターの所有者は、厳密に 1 人許可されます。 `shared_ptr` が必要であることがわかっている場合を除き、POCO の既定のオプションとして使用します。 新しい所有者に移動できますが、コピーおよび共有することはできません。 非推奨とされた `auto_ptr` を置き換えます。 `boost::scoped_ptr` に相当します。 `unique_ptr` 小さく効率的です。サイズは 1 つのポインターを高速な挿入および C++ 標準ライブラリ コレクションから取得するための右辺値参照をサポートしています。 ヘッダー ファイルは `<memory>` です。 詳細については、「[方法 :作成し、unique_ptr インスタンスを使用して](../cpp/how-to-create-and-use-unique-ptr-instances.md)と[unique_ptr クラス](../standard-library/unique-ptr-class.md)します。

- `shared_ptr`<br/>
   参照カウント スマート ポインターです。 複数の所有者に 1 個の生のポインターなどを割り当てる場合に使用します。たとえば、コンテナーからポインターのコピーを返し、元のポインターを維持する場合などです。 生のポインターは、`shared_ptr` のすべての所有者がスコープ外になるか、所有権を放棄するまで削除されません。 サイズはポインター 2 個です。1 個はオブジェクト用で、もう 1 個は参照カウントを含む共有コントロール ブロック用です。 ヘッダー ファイルは `<memory>` です。 詳細については、「[方法 :Shared_ptr インスタンスを作成して](../cpp/how-to-create-and-use-shared-ptr-instances.md)と[shared_ptr クラス](../standard-library/shared-ptr-class.md)します。

- `weak_ptr`<br/>
    `shared_ptr` と同時に使用する特殊ケースのスマート ポインターです。 `weak_ptr` は、1 つ以上の `shared_ptr` インスタンスが所有するオブジェクトへのアクセスを提供しますが、参照カウントには参加しません。 オブジェクトを観察するが、オブジェクトを維持しておく必要はない場合に使用します。 `shared_ptr` インスタンス間の循環参照を解除するいくつかのケースで必要です。 ヘッダー ファイルは `<memory>` です。 詳細については、「[方法 :Weak_ptr インスタンスを作成して](../cpp/how-to-create-and-use-weak-ptr-instances.md)と[weak_ptr クラス](../standard-library/weak-ptr-class.md)します。

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>COM オブジェクト用のスマート ポインター (従来の Windows プログラミング)

COM オブジェクトを使用する場合、スマート ポインターの適切な型でインターフェイス ポインターをラップします。 Active Template Library (ATL) は、さまざまな目的で複数のスマート ポインターを定義します。 さらに、コンパイラが .tlb ファイルからラッパー クラスを作成するときに使用する `_com_ptr_t` スマート ポインターの型を使用することもできます。 これは、ATL ヘッダー ファイルをインクルードしたくない場合に最も適しています。

[CComPtr クラス](../atl/reference/ccomptr-class.md)<br/>
ATL を使用できない場合以外は、これを使用してください。 `AddRef` メソッドと `Release` メソッドを使用して、参照カウントを実行します。 詳細については、「[方法 :作成し、CComPtr および CComQIPtr インスタンスを使用して、](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)します。

[CComQIPtr クラス](../atl/reference/ccomqiptr-class.md)<br/>
`CComPtr` に似ていますが、COM オブジェクトで `QueryInterface` を呼び出すための簡単な構文も提供します。 詳細については、「[方法 :作成し、CComPtr および CComQIPtr インスタンスを使用して、](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)します。

[CComHeapPtr クラス](../atl/reference/ccomheapptr-class.md)<br/>
`CoTaskMemFree` を使用してメモリを解放するオブジェクトへのスマート ポインター。

[CComGITPtr クラス](../atl/reference/ccomgitptr-class.md)<br/>
グローバル インターフェイス テーブル (GIT) から取得されたインターフェイスのスマート ポインターです。

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)<br/>
機能の点では `CComQIPtr` に似ていますが、ATL ヘッダーには依存しません。

### <a name="atl-smart-pointers-for-poco-objects"></a>POCO オブジェクト用の ATL スマート ポインター

COM オブジェクト用のスマート ポインターに加えて、ATL は Plain Old C++ Object 用のスマート ポインター、およびスマート ポインター コレクションも定義します。 特に、コードの移植性が必要でない場合、または C++ 標準ライブラリと ATL のプログラミング モデルを混合しない従来の Windows プログラミングでは、これらの型が、C++ 標準ライブラリ コレクションに便利な代替手段は

[CAutoPtr クラス](../atl/reference/cautoptr-class.md)<br/>
コピー時に所有権を移動することで一意の所有権を強制するスマート ポインターです。 非推奨とされた `std::auto_ptr` クラスに相当します。

[CHeapPtr クラス](../atl/reference/cheapptr-class.md)<br/>
C を使用して割り当てられているオブジェクトのスマート ポインター [malloc](../c-runtime-library/reference/malloc.md)関数。

[CAutoVectorPtr クラス](../atl/reference/cautovectorptr-class.md)<br/>
`new[]` を使用して割り当てられた配列のスマート ポインターです。

[CAutoPtrArray クラス](../atl/reference/cautoptrarray-class.md)<br/>
`CAutoPtr` 要素の配列をカプセル化するクラスです。

[CAutoPtrList クラス](../atl/reference/cautoptrlist-class.md)<br/>
`CAutoPtr` ノードの一覧を操作するメソッドをカプセル化するクラスです。

## <a name="see-also"></a>関連項目

[C++ へようこそ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
