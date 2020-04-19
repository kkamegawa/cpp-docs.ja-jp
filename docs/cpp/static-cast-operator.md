---
title: static_cast 演算子
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: dca6d5297379e6ddc1c70dba80f35f2f55672e49
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267129"
---
# <a name="static_cast-operator"></a>static_cast 演算子

変換、*式*の型に*型 id、* 式に存在する型のみに基づいて。

## <a name="syntax"></a>構文

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Remarks

標準 C++ では、変換の安全性を確認する実行時の型チェックはありません。 C++/CX では、コンパイル時チェックと実行時チェックが実行されます。 詳細については、「 [キャスト](casting.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

**Static_cast**演算子は派生クラスへのポインターを基底クラスへのポインターに変換するなどの操作に使用できます。 このような変換は、必ずしも安全であるとは限りません。

一般的に使用する**static_cast**列挙型などの数値データ型を整数または浮動小数点と整数に変換するときのデータ型の特定のものが、変換に関係します。 **static_cast**の変換はほど安全**dynamic_cast**変換では、ため**static_cast**中は実行時の型チェック、 **dynamic_cast**します。 A **dynamic_cast**あいまいなポインターは失敗し中、 **static_cast**何も問題があります。 これは、危険な場合に返されます。 **Dynamic_cast**変換は安全な**dynamic_cast**のみポインターまたは参照、および実行時の型チェックの動作がのオーバーヘッドが発生します。 詳細については、次を参照してください。 [dynamic_cast Operator](../cpp/dynamic-cast-operator.md)します。

次の例では、`D* pd2 = static_cast<D*>(pb);` は `D` にないフィールドとメソッドがあるため、行 `B` は安全ではありません。 ただし、`B* pb2 = static_cast<B*>(pd);` には `D` のすべてが常に含まれているため、行 `B` は安全な変換です。

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

対照的に[dynamic_cast](../cpp/dynamic-cast-operator.md)で実行時のチェックは行われません、 **static_cast**への変換`pb`します。 `pb` によってポイントされるオブジェクトは、型 `D` のオブジェクトではない場合があります。その場合は、`*pd2` を使用すると、深刻な結果が発生する可能性があります。 たとえば、`D` クラスではなく、`B` クラスのメンバーである関数を呼び出すと、アクセス違反が発生する可能性があります。

**Dynamic_cast**と**static_cast**演算子は、クラス階層全体にポインターを移動します。 ただし、 **static_cast** cast ステートメントで提供される情報に排他的に依存しはそのため安全できません。 例:

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

`pb` が `D` 型のオブジェクトを実際に指し示している場合、`pd1` および `pd2` は同じ値になります。 また、`pb == 0` の場合、同じ値も取得します。

場合`pb`型のオブジェクトを指す`B`とが完全な`D`クラスし**dynamic_cast**十分 0 を返すことがわかります。 ただし、 **static_cast**プログラマのアサーションに依存する`pb`型のオブジェクトを指す`D`、単にその想定されるポインターを返します`D`オブジェクト。

その結果、 **static_cast**暗黙的な変換の逆を行うことができます、この場合、結果は定義されていません。 結果、プログラマがいることを確認する左は、 **static_cast**変換が安全です。

この動作は、クラス型以外の型にも適用されます。 たとえば、 **static_cast**から int に変換するために使用できる、 **char**します。 ただし、その結果、 **char**全体を保持するために十分なビットがない可能性があります**int**値。 ここでも、これは左ことを確認するプログラマからの結果、 **static_cast**変換が安全です。

**Static_cast**演算子が標準変換とユーザー定義の変換を含む、暗黙の変換を実行することもできます。 例:

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

**Static_cast**演算子が列挙型を整数値を明示的に変換できます。 整数型の値が列挙値の範囲内にない場合、結果の列挙値は未定義になります。

**Static_cast**演算子は、null ポインターの値を変換先の型の null ポインター値に変換します。

任意の式は、void 型に明示的に変換できる、 **static_cast**演算子。 変換先の void 型を含めることができます必要に応じて、 **const**、**volatile**、または **_ _unaligned**属性。

**static_cast**演算子はキャストできません、 **const**、**volatile**、または **_ _unaligned**属性。 参照してください[const_cast 演算子](../cpp/const-cast-operator.md)については、これらの属性を削除します。

**C +/CLI CLI:** 次のように再配置を行うガベージ コレクターの使用の先頭で unchecked キャストを実行する危険性のため**static_cast**限定すべきパフォーマンス クリティカルなコードで正しく機能することを確認します。 使用する場合**static_cast**リリース モードで置き換える[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)デバッグ ビルドで成功を確実にします。

## <a name="see-also"></a>関連項目

[キャスト演算子](../cpp/casting-operators.md)<br/>
[キーワード](../cpp/keywords-cpp.md)