---
title: 値型 (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 32cdb29ec1c59081ad7e0493888f290f21561d2b
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220349"
---
# <a name="value-types-modern-c"></a>値型 (Modern C++)

C++ のクラスは、既定値の型では。 このトピックでは、値型と使用に関連する問題の概要を説明します。

## <a name="value-vs-reference-types"></a>値の型と参照型

既に説明したとおり、C++ のクラスは、既定値の型では。 参照型は、オブジェクト指向プログラミングをサポートするポリモーフィックな動作を有効にすると、それらを指定することができます。 値の型は参照型がポリモーフィックな目的の基底クラスと仮想関数の詳細については、メモリとレイアウト コントロールの観点から表示場合があります。 既定では、値型はコピー可能なつまりでは常にコピー コンス トラクターとコピー代入演算子です。 参照型の場合は、クラスにすること、noncopyable (コピー コンス トラクターとコピー代入演算子を無効にする) し、目的のポリモーフィズムをサポートする仮想デストラクターを使用します。 値の型は、コピーされるとき常に提供する個別に変更できる 2 つの独立した値が、内容についてもできます。 参照型は、オブジェクトの種類は、その id の詳細についてはしますか。 このため、「参照の種類」として「ポリモーフィックな型」にも呼ばれます。

ように、コピーを明示的に無効にする必要の参照のような型 (基本クラス、仮想関数) がたい場合、`MyRefType`クラスは、次のコード。

```cpp
// cl /EHsc /nologo /W4

class MyRefType {
private:
    MyRefType & operator=(const MyRefType &);
    MyRefType(const MyRefType &);
public:
    MyRefType () {}
};

int main()
{
    MyRefType Data1, Data2;
    // ...
    Data1 = Data2;
}
```

上記のコードをコンパイルすると、次のエラーが発生します。

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>値型と効率性を移動

新しいコピーの最適化のため、割り当てのコピーのオーバーヘッドが回避されます。 たとえば、文字列のベクターの途中で文字列を挿入するときにされませんコピー再割り当てオーバーヘッドだけ、移動-場合でも、ベクトル自体の成長になります。 これは、たとえば 2 つの非常に大きなオブジェクトの追加操作を実行するその他の操作にも当てはまります。 これらの値の操作の最適化を有効する方法 一部の C++ コンパイラでコンパイラ有効になりますこのが暗黙的に、コピー コンス トラクターは、コンパイラによって自動的に生成できるのと同様にします。 ただし、Visual C では、クラスは「オプトイン」クラスの定義で宣言することにより、割り当てとコンス トラクターを移動する必要があります。 これは、二重のアンパサンドを使用して行われます (& &) 右辺値参照では、適切なメンバー関数の宣言と定義の移動コンス トラクターと移動代入方法。  また、ソース オブジェクトから「心臓を盗もう」正しいコードを挿入する必要があります。

方法を決めるかどうかは、有効になっているを移動する必要がありますか。 既に有効になっている構築をコピーする必要がありますをわかっている場合おそらくするディープ コピーよりも低コストができる場合は、有効な移動します。 ただし、サポートを移動する必要がある場合は、必ずしも限りませんコピーを有効にします。 この後者の場合に「移動のみの型」が呼び出されます。 標準ライブラリで既に例としては、`unique_ptr`します。 ちなみに、古い`auto_ptr`は非推奨にによって置き換えられた`unique_ptr`C の以前のバージョンでの移動セマンティクスのサポートの不足により正確にします。

移動セマンティクスを使用して値渡しの戻り値または挿入、中間のことができます。 この移動は、コピーの最適化です。 回避策としてヒープ割り当ての必要性があります。 次の疑似コードを検討してください。

```cpp
#include <set>
#include <vector>
#include <string>
using namespace std;

//...
set<widget> LoadHugeData() {
    set<widget> ret;
    // ... load data from disk and populate ret
    return ret;
}
//...
widgets = LoadHugeData();   // efficient, no deep copy

vector<string> v = IfIHadAMillionStrings();
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)
//...
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);
//...
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies
```

### <a name="enabling-move-for-appropriate-value-types"></a>適切な値の型の移動を有効にします。

移動をディープ コピーと比べてできる値のようなクラスは、移動の構築を有効にし、効率を高めるための割り当てを移動します。 次の疑似コードを検討してください。

```cpp
#include <memory>
#include <stdexcept>
using namespace std;
// ...
class my_class {
    unique_ptr<BigHugeData> data;
public:
    my_class( my_class&& other )   // move construction
        : data( move( other.data ) ) { }
    my_class& operator=( my_class&& other )   // move assignment
    { data = move( other.data ); return *this; }
    // ...
    void method() {   // check (if appropriate)
        if( !data )
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");
    }
};
```

コピーの構築/割り当てを有効にした場合、詳細コピーよりも低コストができる場合も移動の構築/割り当てを有効にします。

いくつか*非値*の種類は移動専用で、リソースの所有権を転送のみを複製することはできませんとなどです。 例 : `unique_ptr`。

## <a name="section"></a>セクション

Content

## <a name="see-also"></a>関連項目

[C++ 型システム (Modern C++)](../cpp/cpp-type-system-modern-cpp.md)<br/>
[C++ へようこそ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
