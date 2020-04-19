---
title: typeid 演算子
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 93a2d3c494cd5aadafedcaaae9ec72809d633a4a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998750"
---
# <a name="typeid-operator"></a>typeid 演算子

## <a name="syntax"></a>構文

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>コメント

**Typeid**演算子を使用すると、オブジェクトの型を実行時に決定できます。

**Typeid**の結果は `const type_info&`になります。 値は、使用される**typeid**の形式に応じて、*型 id*または*式*の型のいずれかを表す `type_info` オブジェクトへの参照です。 詳細については、「 [Type_info クラス](../cpp/type-info-class.md)」を参照してください。

**Typeid**演算子はマネージ型 (抽象宣言子またはインスタンス) では機能しません。 指定された型の <xref:System.Type> を取得する方法の詳細については、「 [typeid](../extensions/typeid-cpp-component-extensions.md)」を参照してください。

**Typeid**演算子は、ポリモーフィックなクラス型の左辺値に適用される場合にランタイムチェックを実行します。この場合、オブジェクトの実際の型は、指定された静的な情報によって判断されることはありません。 そのようなケースを次に示します。

- クラスへの参照

- `*` で逆参照されるポインター。

- 添字ポインター (`[ ]`)。 (ポリモーフィックな型へのポインターで添字を使用するのは安全ではありません)。

*式*が基底クラス型を指していても、オブジェクトがその基底クラスから派生した型である場合は、派生クラスの `type_info` 参照が結果になります。 *式*はポリモーフィック型 (仮想関数を持つクラス) を指す必要があります。 それ以外の場合、結果は、*式*で参照されている静的クラスの `type_info` になります。 また、ポインターを逆参照する必要があります。これにより、使用されるオブジェクトが参照先のオブジェクトになります。 ポインターを逆参照しない場合、結果はポインターが指すものではなく、ポインターの `type_info` になります。 例 :

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

*式*がポインターを逆参照していて、そのポインターの値が0である場合、 **typeid**は[bad_typeid 例外](../cpp/bad-typeid-exception.md)をスローします。 ポインターが有効なオブジェクトを指していない場合は、`__non_rtti_object` 例外がスローされます。 オブジェクトが無効であるためにエラーをトリガーした RTTI の分析が試行されたことを示します。 (たとえば、無効なポインターであるか、またはコードが[/gr](../build/reference/gr-enable-run-time-type-information.md)でコンパイルされていません)。

*式*がオブジェクトの基底クラスへの参照ではなくポインターではない場合、結果は*式*の静的な型を表す `type_info` 参照になります。 式の*静的な型*は、コンパイル時に認識される式の型を参照します。 実行セマンティクスは、式の静的な型を評価するときは無視されます。 さらに、式の静的な型を判断するときに、参照は可能な限り無視されます。

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

テンプレートで**typeid**を使用して、テンプレートパラメーターの種類を決定することもできます。

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>参照

[ランタイム型情報](../cpp/run-time-type-information.md)\
[キーワード](../cpp/keywords-cpp.md)
