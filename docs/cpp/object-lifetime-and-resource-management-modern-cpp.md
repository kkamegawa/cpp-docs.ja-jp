---
title: オブジェクトの有効期間とリソースの管理 (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 5964078960a5b241cb5af369aeddba45a06e48ad
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220632"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>オブジェクトの有効期間とリソースの管理 (Modern C++)

管理対象の言語とは異なり、C++ はプログラムを実行すると、いいえ-長い-使用メモリ リソースを自動的に解放するガベージ コレクション (GC) がありません。 C++ では、リソースの管理に直接関連するオブジェクトの有効期間。 このドキュメントでは、C++ では、オブジェクトの有効期間および管理する方法に影響する要因について説明します。

C++ で、非メモリ リソースを処理しないため、主に、GC がない場合があります。 のみ C++ のような確定的なデストラクターはメモリと非メモリ リソースを均等に処理できます。 GC はメモリと CPU 使用量、および局所性の高いオーバーヘッドなどの他の問題もあります。 一般性、巧みな最適化によって軽減することはできません、根本的な問題です。

## <a name="concepts"></a>概念

オブジェクト有効期間の管理で、重要な点は、カプセル化: オブジェクト リソースを所有する、または、それらを削除する方法またはでもかどうか、所有するすべてのリソースすべてを知る必要がありませんすべてのユーザーがオブジェクトを使用しています。 オブジェクトを破棄するだけですがあります。 C++ のコア言語がオブジェクトは、適切なタイミングには、破棄されたことを確認するように設計ブロックが終了して、逆の順序で構築のようにします。 オブジェクトが破棄されると、その基底クラスとメンバーが特定の順序で破棄されます。  言語は、ヒープの割り当てまたは新しい配置のような特別な処理を行う場合を除き、自動的に、オブジェクトを破棄します。  たとえば、[スマート ポインター](../cpp/smart-pointers-modern-cpp.md)など`unique_ptr`と`shared_ptr`などの C++ 標準ライブラリ コンテナーと`vector`、カプセル化**新しい**/ **削除**と`new[]` / `delete[]`オブジェクトのデストラクターであります。 理由がスマート ポインターと C++ 標準ライブラリ コンテナーを使用するために重要です。

有効期間管理におけるもう 1 つの重要な概念: デストラクター。 デストラクターは、リソースのリリースをカプセル化します。  (一般的に使用されるニーモニックは RRID、リソースのリリースが破棄です)。リソースは、"system"から取得し、後でバックアップを提供する必要があることです。  メモリは、最も一般的なリソースが、ファイル、ソケット、テクスチャ、およびその他の非メモリ リソースもがあります。 リソースを"所有"している必要があることができる場合にも操作を終了したら、リリースを使用することができますを意味します。  オブジェクトが破棄されるときに、デストラクターは、所有するリソースを解放します。

最終的な概念は、DAG (有向非循環有向グラフ) です。  プログラム内の所有権の構造は、DAG を形成します。 オブジェクトを所有できるありません自体などないのみが不可能でも本質的に意味のないです。 ただし、2 つのオブジェクトは、3 番目のオブジェクトの所有権を共有できます。  このような DAG ではいくつかの種類のリンクです。A が B のメンバー (B は、A を所有する、) C ストア、 `vector<D>` (C は、D の各要素を所有する、) E ストア、 `shared_ptr<F>` (E、F の所有権可能性がありますと共有の他のオブジェクト) など。  循環がないと、DAG 内のすべてのリンクは、オブジェクトによって表される限り、(生のポインター、ハンドル、またはその他のメカニズム) 代わりにデストラクターを持つし、言語が原因であるために、リソースのリークにことはできません。 リソースは、必要なくなったら、ガベージ コレクターが実行されていることがなく後すぐに解放されます。 追跡の有効期間は、スタックのスコープ、ベース、メンバー、および関連する場合は、のオーバーヘッドが無料かつ安価`shared_ptr`します。

### <a name="heap-based-lifetime"></a>ヒープ ベースの有効期間

ヒープ オブジェクトの有効期間を使用して[スマート ポインター](../cpp/smart-pointers-modern-cpp.md)します。 使用`shared_ptr`と`make_shared`として既定のポインターとアロケーター。 使用`weak_ptr`サイクルを中断、キャッシュを実行に影響を与えるか、有効期間について何もせずにオブジェクトを確認しています。

```cpp
void func() {

auto p = make_shared<widget>(); // no leak, and exception safe
...
p->draw();

} // no delete required, out-of-scope triggers smart pointer destructor
```

使用`unique_ptr`の一意の所有権など、 *pimpl*表現形式です。 (を参照してください[コンパイル時のカプセル化の Pimpl](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md))。ように、`unique_ptr`明示的なすべての主なターゲット**新しい**式。

```cpp
unique_ptr<widget> p(new widget());
```

所有権がないと観察の生のポインターを使用できます。 所有している以外のポインターが使われますしますが、リークが発生することはできません。

```cpp
class node {
  ...
  vector<unique_ptr<node>> children; // node owns children
  node* parent; // node observes parent, which is not a concern
  ...
};
node::node() : parent(...) { children.emplace_back(new node(...) ); }
```

パフォーマンスの最適化が必要な場合は、使用する必要があります*適切にカプセル化された*ポインターおよび削除する明示的な呼び出しを所有しています。 例では、独自の下位レベルのデータ構造を実装する場合です。

### <a name="stack-based-lifetime"></a>スタック ベースの有効期間

最新の c++*スタック ベースのスコープ*自動組み合わせるために堅牢なコードを記述する強力な方法は、*スタックの有効期間*と*データ メンバーの有効期間*高効率で。追跡の有効期間はオーバーヘッドの本質的には無料です。 ヒープ オブジェクトの有効期間は、入念な手動による管理を必要とし、生のポインターを使用する場合は特に、リソースのリーク、非効率性のソースを指定できます。 このコードでは、スタック ベースのスコープを示しますを検討してください。

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

静的な有効期間を多用しない (グローバル静的、関数のローカルの静的な) 問題が発生する可能性があるためです。 グローバル オブジェクトのコンス トラクターが例外をスローすると起こりますか。 通常、デバッグが困難に可能性のある方法でのアプリ エラー。 構築の順序は、静的な有効期間オブジェクトでは問題と、同時実行セーフではありません。 オブジェクトの構築は、問題だけでなく、ポリモーフィズムが必要な場合に特に、破棄の順序が複雑になることができます。 オブジェクトまたは変数は、ポリモーフィックななく複雑なコンストラクション/デストラクションの順序付けがない、場合でも、スレッド セーフな同時実行の問題は引き続き存在します。 マルチ スレッド アプリは、スレッド ローカル ストレージ リソースのロックやその他の特別な予防策をしなくても静的オブジェクトのデータを安全に変更できません。

## <a name="see-also"></a>関連項目

[C++ へようこそ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
