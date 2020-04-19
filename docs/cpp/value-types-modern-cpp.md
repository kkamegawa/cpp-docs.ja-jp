---
title: 値の型としての C++ クラス
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 1aabcad46e848e1a499a142adaba5002a829bbf5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246018"
---
# <a name="c-classes-as-value-types"></a>値の型としての C++ クラス

C++クラスは、既定値の型になります。 これらは参照型として指定できます。これにより、ポリモーフィックな動作によってオブジェクト指向プログラミングがサポートされるようになります。 値型は、メモリとレイアウトコントロールの観点から見ることができます。一方、参照型は、ポリモーフィックな目的で基底クラスと仮想関数に関するものです。 既定では、値型はコピー可能です。つまり、コピーコンストラクターとコピー代入演算子が常に存在することを意味します。 参照型の場合は、クラスを非コピー可能にし (コピーコンストラクターとコピー代入演算子を無効にし)、目的のポリモーフィズムをサポートする仮想デストラクターを使用します。 値の型もコンテンツに関するものであり、コピーされるときには、個別に変更できる2つの独立した値を常に提供します。 参照型は id に関するものです。オブジェクトの種類は何ですか。 このため、"参照型" は "ポリモーフィックな型" とも呼ばれます。

参照のような型 (基底クラス、仮想関数) が本当に必要な場合は、次のコードの `MyRefType` クラスに示すように、コピーを明示的に無効にする必要があります。

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

## <a name="value-types-and-move-efficiency"></a>値の種類と移動の効率

新しいコピーの最適化により、コピー割り当てのオーバーヘッドが回避されます。 たとえば、文字列のベクトルの途中に文字列を挿入した場合、コピーの再割り当てのオーバーヘッドは発生せず、移動だけで、ベクター自体が拡大する場合でも同様です。 これは、他の操作にも適用されます。たとえば、2つの非常に大きなオブジェクトに対して追加操作を実行する場合です。 これらの値操作の最適化を有効にするにはどうすればよいですか。 一部C++のコンパイラでは、コンパイラによってコピーコンストラクターが自動的に生成されるのと同じように、コンパイラが暗黙的にこれを有効にします。 ただし、でC++は、クラス定義で宣言することによって、割り当てとコンストラクターを移動するために、クラスは "オプトイン" を行う必要があります。 これを実現するには、適切なメンバー関数の宣言で二重アンパサンド (& &) 右辺値参照を使用し、移動コンストラクターと移動代入メソッドを定義します。  また、正しいコードを挿入して、ソースオブジェクトの外部に "内容" を追加する必要もあります。

移動が有効になっているかどうかを判断するにはどうすればよいですか。 コピーの構築が有効になっていることがわかっている場合は、詳細コピーよりも安価な場合は、移動を有効にすることをお勧めします。 ただし、移動サポートが必要であることがわかっている場合は、コピーが有効になっていることを意味するわけではありません。 後者の場合は、"移動のみの型" と呼ばれます。 標準ライブラリに既に存在する例は、`unique_ptr`です。 ただし、以前のバージョンのC++では、移動セマンティクスがサポートされていないため、古い `auto_ptr` は非推奨とされ、`unique_ptr` に置き換えられました。

移動セマンティクスを使用することによって、値渡しまたは挿入途中で返すことができます。 Move は copy の最適化です。 回避策として、ヒープ割り当てが必要です。 次の擬似コードを考えてみましょう。

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

### <a name="enabling-move-for-appropriate-value-types"></a>適切な値型の移動の有効化

値に似たクラスで、移動が詳細コピーよりも安価な場合は、移動の構築と移動の割り当てを有効にします。 次の擬似コードを考えてみましょう。

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

コピーの構築/割り当てを有効にした場合は、詳細コピーよりも安価な場合は、[構築/割り当ての移動] も有効にします。

一部の*値以外*の型は移動のみです。たとえば、リソースを複製できず、所有権を移転する場合にのみ使用されます。 例 : `unique_ptr`。

## <a name="see-also"></a>参照

[C++型システム](../cpp/cpp-type-system-modern-cpp.md)<br/>
[に戻るC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
