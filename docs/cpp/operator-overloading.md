---
title: 演算子のオーバーロード
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: d6a294af3ea7ef6085eae0f7069ea2d1fdbb30e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377362"
---
# <a name="operator-overloading"></a>演算子のオーバーロード

**演算子**キーワードが指定する関数を宣言*演算子記号*クラスのインスタンスに適用されるときのことを意味します。 これによって、演算子に複数の意味を与えます (つまり、"オーバーロード" します)。 コンパイラは、オペランドの型を検査することにより、演算子の異なる意味を区別します。

## <a name="syntax"></a>構文

> *type* **operator** *operator-symbol* **(** *parameter-list* **)**

## <a name="remarks"></a>Remarks

ほとんどの組み込み演算子の関数をグローバルに、またはクラス単位で定義し直すことができます。 オーバーロードされた演算子は、関数として実装されます。

オーバー ロードされた演算子の名前は**演算子** *x*ここで、 *x*演算子は、次の表に表示されます。 という名前の関数を定義する加算演算子をオーバー ロードには、たとえば、 **operator +** します。 同様に、加算/代入演算子をオーバー ロードする **+=** 、呼び出される関数を定義**演算子 + =** します。

### <a name="redefinable-operators"></a>再定義可能な演算子

|演算子|名前|型|
|--------------|----------|----------|
|**、**|コンマ|2 項|
|**\!**|論理 NOT|単項|
|**\!=**|非等値|2 項|
|**%**|剰余|2 項|
|**%=**|剰余代入|2 項|
|**&**|ビットごとの AND|2 項|
|**&**|アドレス取得|単項|
|**&&**|論理 AND|2 項|
|**&=**|ビットごとの AND 代入|2 項|
|**( )**|関数呼び出し|—|
|**( )**|キャスト演算子|単項|
|**&#42;**|乗算|2 項|
|**&#42;**|ポインター逆参照|単項|
|**&#42;=**|乗算代入|2 項|
|**+**|加算|2 項|
|**+**|単項プラス|単項|
|**++**|インクリメント<sup>1</sup>|単項|
|**+=**|加算代入|2 項|
|**-**|減算|2 項|
|**-**|単項マイナス符号|単項|
|**--**|デクリメント<sup>1</sup>|単項|
|**-=**|減算代入|2 項|
|**->**|メンバー選択|2 項|
|**->&#42;**|メンバーへのポインター選択|2 項|
|**/**|除算記号|2 項|
|**/=**|除算代入|2 項|
|**\<**|より小さい|2 項|
|**<<**|左シフト|2 項|
|**<<=**|左シフト代入|2 項|
|**<=**|次の値以下|2 項|
|**=**|代入|2 項|
|**==**|等価比較|2 項|
|**>**|次の値より大きい|2 項|
|**>=**|次の値以上|2 項|
|**>>**|右シフト|2 項|
|**>>=**|右シフト代入|2 項|
|**[ ]**|配列添字|—|
|**^**|排他的 OR|2 項|
|**^=**|排他的 OR 代入|2 項|
|**&#124;**|ビットごとの包括的 OR|2 項|
|**&#124;=**|ビットごとの包括的 OR 代入|2 項|
|**&#124;&#124;**|論理 OR|2 項|
|**~**|1 の補数|単項|
|**delete**|削除|—|
|**new**|新規作成|—|
|変換演算子|変換演算子|単項|

<sup>1</sup> 2 つのバージョンの単項インクリメントおよびデクリメント演算子: 前置インクリメントと後置インクリメント。

参照してください[演算子のオーバー ロードに関する一般的な規則](../cpp/general-rules-for-operator-overloading.md)詳細についてはします。 さまざまなカテゴリのオーバーロードされた演算子に対する制約については、次のトピックを参照してください。

- [単項演算子](../cpp/overloading-unary-operators.md)

- [二項演算子](../cpp/binary-operators.md)

- [代入](../cpp/assignment.md)

- [関数呼び出し](../cpp/function-call-cpp.md)

- [添字演算子](../cpp/subscripting.md)

- [クラス メンバーへのアクセス](../cpp/member-access.md)

- [インクリメントとデクリメント](../cpp/increment-and-decrement-operator-overloading-cpp.md)します。

- [ユーザー定義型の変換](../cpp/user-defined-type-conversions-cpp.md)

次のテーブルに示す演算子は、オーバーロードできません。 テーブルには、プリプロセッサ シンボルが含まれています。 **#** と **##** します。

### <a name="nonredefinable-operators"></a>再定義不可演算子

|演算子|名前|
|-|-|
|**.**|メンバー選択|
|**.&#42;**|メンバーへのポインター選択|
|**::**|スコープ解決|
|**? :**|条件|
|**#**|プリプロセッサによる文字列への変換|
|**##**|プリプロセッサによる連結|

オーバーロードされた演算子は通常、コードに出現すると、コンパイラによって暗黙的に呼び出されますが、メンバーまたは非メンバー関数を呼び出すのと同じ方法で明示的に呼び出すことができます。

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>例

次の例のオーバー ロード、 **+** 演算子を 2 つの複素数の数値し、結果を返します。

```cpp
// operator_overloading.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Complex {
   Complex( double r, double i ) : re(r), im(i) {}
   Complex operator+( Complex &other );
   void Display( ) {   cout << re << ", " << im << endl; }
private:
   double re, im;
};

// Operator overloaded using a member function
Complex Complex::operator+( Complex &other ) {
   return Complex( re + other.re, im + other.im );
}

int main() {
   Complex a = Complex( 1.2, 3.4 );
   Complex b = Complex( 5.6, 7.8 );
   Complex c = Complex( 0.0, 0.0 );

   c = a + b;
   c.Display();
}
```

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>このセクションの内容

- [演算子のオーバーロードに関する一般的な規則](../cpp/general-rules-for-operator-overloading.md)

- [単項演算子のオーバーロード](../cpp/overloading-unary-operators.md)

- [二項演算子](../cpp/binary-operators.md)

- [代入](../cpp/assignment.md)

- [関数呼び出し](../cpp/function-call-cpp.md)

- [添字演算子](../cpp/subscripting.md)

- [メンバー アクセス](../cpp/member-access.md)

## <a name="see-also"></a>関連項目

[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[キーワード](../cpp/keywords-cpp.md)