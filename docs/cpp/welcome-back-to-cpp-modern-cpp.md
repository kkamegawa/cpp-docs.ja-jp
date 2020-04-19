---
title: モダンにC++戻るC++
description: 最新C++のプログラミングの表現方法とその原理について説明します。
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 9630322024e639f9e5db1888dac5a1530befc716
ms.sourcegitcommit: ba129dc55dc3ff638f3af5ac0e87ec2ca1cb2674
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869722"
---
# <a name="welcome-back-to-c---modern-c"></a>モダンにC++戻るC++

作成以来、 C++は世界で最も広く使用されているプログラミング言語の1つになりました。 適切に記述された C++ プログラムは、高速で効率的です。 言語は他の言語よりも柔軟です。これは、最高レベルの抽象化で動作したり、シリコンのレベルでダウンしたりすることができます。 C++は、高度に最適化された標準ライブラリを提供します。 低レベルのハードウェア機能にアクセスして、速度を最大化し、メモリ要件を最小限に抑えることができます。 をC++使用すると、幅広いアプリを作成できます。 ゲーム、デバイスドライバー、およびハイパフォーマンス科学ソフトウェア。 埋め込みプログラム。 Windows クライアントアプリ。 他のプログラミング言語用のライブラリやコンパイラも、 C++で記述されています。

C++ の最初の要件の 1 つは、C 言語との下位互換性でした。 その結果、にC++は常に、生のポインター、配列、null で終わる文字列、およびその他の機能を持つ C スタイルのプログラミングが許可されています。 優れたパフォーマンスを実現しますが、バグや複雑さを発生させることもできます。 の進化にC++より、C スタイルの表現を使用する必要性が大幅に減少する機能が強調されています。 以前の C プログラミング機能は必要なときには存在しますが、 C++最新のコードでは、これらの機能を小さくする必要があります。 最新C++のコードは、よりシンプルで安全性が高く、洗練されています。

次のセクションでは、最新C++のの主な機能の概要について説明します。 特に明記されていない限り、ここに記載されている機能は C++ 11 以降で使用できます。 Microsoft C++コンパイラでは、 [/std](../build/reference/std-specify-language-standard-version.md)コンパイラオプションを設定して、プロジェクトに使用する標準のバージョンを指定できます。

## <a name="resources-and-smart-pointers"></a>リソースとスマートポインター

C スタイルのプログラミングにおけるバグの主要なクラスの1つは、*メモリリーク*です。 多くの場合、リークは、 **new**で割り当てられたメモリの**delete**の呼び出しに失敗したことが原因で発生します。 現代C++で*は、リソース取得は初期化*(RAII) の原則が強調されています。 アイデアは単純です。 リソース (ヒープメモリ、ファイルハンドル、ソケットなど) は、オブジェクトによって*所有*されている必要があります。 そのオブジェクトは、新しく割り当てられたリソースをそのコンストラクター内で作成または受信し、デストラクター内で削除します。 RAII の原則により、所有しているオブジェクトがスコープ外になったときに、すべてのリソースがオペレーティングシステムに適切に返されることが保証されます。

RAII の原則を簡単に導入できるようC++に、標準ライブラリには、 [std:: unique_ptr](../standard-library/unique-ptr-class.md)、 [std:: shared_ptr](../standard-library/shared-ptr-class.md)、 [std:: weak_ptr](../standard-library/weak-ptr-class.md)の3種類のスマートポインターが用意されています。 スマートポインターは、所有しているメモリの割り当てと削除を処理します。 次の例は、`make_unique()`への呼び出しでヒープに割り当てられた配列メンバーを持つクラスを示しています。 **New**と**delete**の呼び出しは、`unique_ptr` クラスによってカプセル化されます。 `widget` オブジェクトがスコープ外に出ると、unique_ptr デストラクターが呼び出され、配列に割り当てられたメモリが解放されます。  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

可能な限り、ヒープメモリを割り当てるときにスマートポインターを使用します。 New 演算子と delete 演算子を明示的に使用する必要がある場合は、RAII の原則に従ってください。 詳細については、「[オブジェクトの有効期間とリソースの管理」 (RAII)](object-lifetime-and-resource-management-modern-cpp.md)を参照してください。

## <a name="stdstring-and-stdstring_view"></a>std:: string および std:: string_view

C スタイルの文字列は、バグのもう1つの主要な原因です。 [Std:: string および std:: wstring](../standard-library/basic-string-class.md)を使用すると、C スタイルの文字列に関連するすべてのエラーを取り除くことができます。 検索、追加、前処理などのメンバー関数の利点も得られます。 どちらも速度に対して高度に最適化されています。 読み取り専用アクセスのみを必要とする関数に文字列を渡す場合は、C++ 17 で[std:: string_view](../standard-library/basic-string-view-class.md)を使用すると、さらに優れたパフォーマンスを得ることができます。

## <a name="stdvector-and-other-standard-library-containers"></a>std:: vector とその他の標準ライブラリコンテナー

標準ライブラリのコンテナーはすべて、RAII の原則に従います。 要素を安全に検査するための反復子を提供します。 また、パフォーマンスに対して高度に最適化され、正確なテストが行われています。 これらのコンテナーを使用することにより、カスタムデータ構造で導入される可能性があるバグや非効率性を排除できます。 Raw 配列ではなく、[ベクター](../standard-library/vector-class.md)をのC++シーケンシャルコンテナーとして使用します。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

既定の連想コンテナー として [map](../standard-library/map-class.md) (not `unordered_map`) を使用します。 低次元と複数のケースには、 [set](../standard-library/set-class.md)、 [multimap](../standard-library/multimap-class.md)、およびマルチ[セット](../standard-library/multiset-class.md)を使用します。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

パフォーマンスの最適化が必要な場合は、次の使用を検討します。

- たとえば、クラスメンバーとして埋め込む場合の[配列](../standard-library/array-class-stl.md)型。

- [Unordered_map](../standard-library/unordered-map-class.md)などの順序付けられていない連想コンテナー。 これらの要素には、要素ごとのオーバーヘッドが少なく、一定時間の参照がありますが、正確で効率的に使用するのは困難な場合があります。

- 並べ替えられた `vector`。 詳細については、「[アルゴリズム](../cpp/algorithms-modern-cpp.md)」をご覧ください。

C スタイルの配列は使用しないでください。 データへの直接アクセスを必要とする古い Api の場合は、代わりに `f(vec.data(), vec.size());` などのアクセサーメソッドを使用します。 コンテナーの詳細については、「 [ C++標準ライブラリコンテナー](../standard-library/stl-containers.md)」を参照してください。

## <a name="standard-library-algorithms"></a>標準ライブラリのアルゴリズム

プログラムのカスタムアルゴリズムを記述する必要があると想定する前に、まず標準C++ライブラリの[アルゴリズム](../standard-library/algorithm.md)を確認してください。 標準ライブラリには、検索、並べ替え、フィルター処理、ランダム化するなど、多くの一般的な操作について、増え続けるアルゴリズムが含まれています。 数値演算ライブラリは広範囲にわたっています。 C++ 17 以降では、多くのアルゴリズムの並列バージョンが提供されています。

次に重要な例を示します。

- **for_each**、既定のトラバーサルアルゴリズム (および範囲ベースの for ループ) です。

- **変換**(コンテナー要素のインプレース変更の場合)

- **find_if**、既定の検索アルゴリズムです。

- **sort**、 **lower_bound**、およびその他の既定の並べ替えと検索アルゴリズム。

比較子を記述するには、狭義の **<** と *名前付きラムダ* を使用することができます。

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>明示的な型名ではなく auto

C++ 11 では、変数、関数、およびテンプレート宣言で使用する[auto](auto-cpp.md)キーワードが導入されました。 **auto**は、明示的に入力する必要がないように、オブジェクトの型を推測するようにコンパイラに指示します。 **auto**は、推測された型が入れ子になったテンプレートの場合に特に便利です。

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>範囲ベースの for ループ

配列とコンテナーに対する C スタイルの反復処理では、インデックス作成エラーが発生する可能性があり、型の場合もあります。 これらのエラーを回避し、コードを読みやすくするには、標準ライブラリのコンテナーと生の配列の両方を含む範囲ベースの for ループを使用します。 詳細については、「[範囲ベースの for ステートメント](../cpp/range-based-for-statement-cpp.md)」を参照してください。

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>マクロではなく constexpr 式

C とC++のマクロは、コンパイルの前にプリプロセッサによって処理されるトークンです。 マクロトークンの各インスタンスは、ファイルがコンパイルされる前に定義された値または式に置き換えられます。 マクロは、コンパイル時の定数値を定義するために、一般的に C スタイルのプログラミングで使用されます。 ただし、マクロはエラーが発生しやすく、デバッグが困難です。 現代C++では、コンパイル時の定数に[constexpr](constexpr-cpp.md)変数を使用することをお勧めします。

```cpp
#define SIZE 10 / C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>一様初期化

モダンC++では、任意の型に対して中かっこの初期化を使用できます。 この形式の初期化は、配列、ベクター、またはその他のコンテナーを初期化するときに特に便利です。 次の例では、`v2` が `S`の3つのインスタンスで初期化されます。 `v3` は、中かっこを使用して初期化される `S` の3つのインスタンスで初期化されます。 コンパイラは、宣言された `v3`の型に基づいて、各要素の型を推測します。

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

詳細については、「中[かっこの初期化](initializing-classes-and-structs-without-constructors-cpp.md)」を参照してください。

## <a name="move-semantics"></a>移動セマンティクス

モダンC++は*移動セマンティクス*を提供し、不要なメモリコピーを排除できるようにします。 以前のバージョンの言語では、特定の状況ではコピーが回避されていました。 *移動*操作では、コピーを作成せずに、リソースの所有権を1つのオブジェクトから次のオブジェクトに転送します。 リソース (ヒープメモリ、ファイルハンドルなど) を所有するクラスを実装する場合は、*移動コンストラクター*と*移動代入演算子*を定義できます。 コンパイラは、コピーが不要な場合に、オーバーロードの解決時にこれらの特殊なメンバーを選択します。 標準ライブラリのコンテナー型は、オブジェクトが定義されている場合、その移動コンストラクターを呼び出します。 詳細については、「[移動コンストラクターと移動代入C++演算子 ()](move-constructors-and-move-assignment-operators-cpp.md)」を参照してください。

## <a name="lambda-expressions"></a>ラムダ式

C スタイルのプログラミングでは、関数*ポインター*を使用して、関数を別の関数に渡すことができます。 関数ポインターは、維持して理解するのに不便です。 参照する関数は、呼び出し元の時点から遠く離れた場所にソースコード内の他の場所で定義できます。 また、タイプセーフではありません。 モダンC++に*は、* [()](function-call-operator-parens.md)演算子をオーバーライドするクラスが用意されています。これにより、関数と同様に呼び出すことができます。 関数オブジェクトを作成する最も便利な方法は、インライン[ラムダ式](../cpp/lambda-expressions-in-cpp.md)を使用することです。 次の例は、ラムダ式を使用して関数オブジェクトを渡す方法を示しています。この関数は、ベクター内の各要素に対して `for_each` 関数が呼び出します。

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

ラムダ式の `[=](int i) { return i > x && i < y; }` は、"型 `int` の1つの引数を受け取る関数として読み取ることができ、引数が `y``x` より大きいかどうかを示すブール値を返します。 ラムダでは、周囲のコンテキストから `x` と `y` 変数を使用できることに注意してください。 `[=]` は、これらの変数が値によって*キャプチャ*されることを指定します。つまり、ラムダ式には、それらの値の独自のコピーがあります。

## <a name="exceptions"></a>例外

モダンC++では、エラー状態を報告および処理する最良の方法として、エラーコードではなく例外が強調されています。 詳細については、「[例外とエラー処理の最新C++のベストプラクティス](errors-and-exception-handling-modern-cpp.md)」を参照してください。

## <a name="stdatomic"></a>std:: atomic

標準ライブラリC++ [std:: atomic](../standard-library/atomic-structure.md)構造体と、スレッド間の通信メカニズムに関連する型を使用します。

## <a name="stdvariant-c17"></a>std:: variant (C++ 17)

共用体は、さまざまな型のメンバーが同じメモリ位置を占有できるようにすることで、メモリを節約するために C スタイルのプログラミングでよく使用されます。 ただし、共用体はタイプセーフではなく、プログラミングエラーを引き起こす可能性があります。 C++ 17 では、 [std:: variant](../standard-library/variant-class.md)クラスが、共用体のより堅牢で安全な代替手段として導入されています。 [Std:: visit](../standard-library/variant-functions.md#visit)関数を使用すると、タイプセーフな方法で `variant` 型のメンバーにアクセスできます。

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)\
[ラムダ式](../cpp/lambda-expressions-in-cpp.md)\
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)\
[Microsoft C++ 言語の準拠表](../overview/visual-cpp-language-conformance.md)
