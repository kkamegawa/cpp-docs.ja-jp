---
title: コピー コンストラクターとコピー代入演算子 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: 59f463d103e233a1d9b25da3243a16f67263c815
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392298"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>コピー コンストラクターとコピー代入演算子 (C++)

> [!NOTE]
> C++ 11 以降、2 種類の代入が言語でサポートされて:*コピー割り当て*と*移動の代入*します。 この記事では、特に明示的に記載しない限り、"代入" はコピーの代入を意味します。 移動代入については、次を参照してください。[移動コンス トラクターと移動代入演算子 (C++)](move-constructors-and-move-assignment-operators-cpp.md)します。
>
> 代入演算と初期化操作では、いずれもオブジェクトがコピーされます。

- **割り当て**:1 つのオブジェクトの値が別のオブジェクトに割り当てられると、最初のオブジェクトは、2 番目のオブジェクトにコピーされます。 次に例を示します。

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   の場合、`b` の値が `a` にコピーされます。

- **初期化**:初期化は、引数は、値によって関数に渡されるときに、新しいオブジェクトが宣言されたとき、または値が値によって関数から返されるときに発生します。

クラス型のオブジェクトに「コピー」の意味を定義できます。 たとえば、次のコードについて考えます。

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

前のコードは、「FILE1.DAT から FILE2.DAT に内容をコピーする」を意味する場合もありますが、「FILE2.DAT を無視して `b` を FILE1.DAT への 2 番目のハンドルにする」という意味もあります。 各クラスには、次のように適切なコピーのセマンティクスを割り当てる必要があります。

- 代入演算子を使用して**演算子 =** 戻り値の型として渡されるパラメーターとしてクラス型への参照と共に**const**参照 — たとえば`ClassName& operator=(const ClassName& x);`します。

- コピー コンストラクターを使用する。

コピー コンストラクターを宣言していない場合、コンパイラはメンバーごとのコピー コンストラクターを生成します。  コピー代入演算子を宣言していない場合、コンパイラはメンバーごとのコピー代入演算子を生成します。 コピー コンストラクターを宣言しても、コンパイラで生成されるコピー代入演算子は抑制されません。また、その逆も同様です。 いずれか 1 つを実装する場合、コードの意味を明確にするために、もう 1 つも実装することをお勧めします。

コピー コンス トラクターが型の引数を受け取る<em>クラス名</em><strong>&</strong>ここで、*クラス名*コンス トラクターが定義されているクラスの名前を指定します。 例えば:

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> コピー コンス トラクターの引数の型を行う**const** <em>クラス名</em><strong>&</strong>可能な場合。 これによって、コピー コンストラクターが誤ってコピー元のオブジェクトを変更しないようにすることができます。 コピーすることもできます**const**オブジェクト。

## <a name="compiler-generated-copy-constructors"></a>コンパイラによって生成されたコピー コンストラクター

ユーザー定義のコピー コンス トラクターのように、コンパイラによって生成されたコピー コンス トラクターがある型の 1 つの引数"への参照*クラス名*"。 すべての基底クラスとメンバーのクラス型の 1 つの引数の取得として宣言されたコピー コンス トラクターがある場合は、例外**const** <em>クラス名</em><strong>&</strong>します。 このような場合は、コンパイラによって生成されたコピー コンス トラクターの引数も**const**します。

コピー コンス トラクターに引数の型がない場合**const**、コピーによる初期化を**const**オブジェクト、エラーが発生します。 逆は true ではありません。引数が場合**const**、初期化するにはないオブジェクトのコピーで**const**。

コンパイラによって生成された代入演算子に関して同じパターンに従います**const です。** 型の 1 つの引数をとる<em>クラス名</em><strong>&</strong>すべて基底クラスおよびメンバー クラスの代入演算子は、型の引数を受け取らない**const** <em>クラス名</em><strong>&</strong>します。 クラスの代入演算子を生成されたここで、 **const**引数。

> [!NOTE]
> コピー コンストラクターによって初期化されるか、コンパイラによって生成されるか、またはユーザーによって定義される場合、仮想基底クラスは構築される時点で 1 回だけ初期化されます。

影響はコピー コンストラクターの影響と似ています。 引数の型がない**const**からの割り当て、 **const**オブジェクト、エラーが発生します。 逆は true ではありません。場合、 **const**値がない値に割り当てられている**const**割り当てが成功するとします。

オーバー ロードされた代入演算子の詳細については、次を参照してください。[割り当て](../cpp/assignment.md)します。