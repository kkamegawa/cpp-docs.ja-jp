---
title: '方法: ジェネリックを使用してパフォーマンスを改善する (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 958da08716022bedaa8d0fe217814fa2bd86c065
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515717"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>方法: ジェネリックを使用してパフォーマンスを改善する (C++/CLI)

ジェネリックを使用して、型パラメーターに基づく再利用可能なコードを作成できます。 型パラメーターの実際の型は、クライアント コードによって呼び出されるまで遅延されます。 ジェネリックの詳細については、「 [Generics](generics-cpp-component-extensions.md)」を参照してください。

この記事では、コレクションを使用するアプリケーションのパフォーマンスを向上させるのにジェネリックがどのように役立つかについて説明します。

## <a name="example"></a>例

.NET Framework には、<xref:System.Collections?displayProperty=fullName> 名前空間内に多数のコレクション クラスが付属しています。 これらのコレクションのほとんどは、<xref:System.Object?displayProperty=fullName> 型のオブジェクトで動作します。 これにより、.NET Framework の型は、値の型も含めて、すべて <xref:System.Object?displayProperty=fullName> から派生するため、任意の型をコレクションに格納できます。 ただし、この方法には 2 つの欠点があります。

1 つ目は、整数などの値型がコレクションに格納される場合は、コレクションに追加される前に値をボックス化し、コレクションから値が取得されるときにボックス化解除する必要があることです。 これらは負荷の高い操作です。

2 つ目は、コレクションに追加できる型を制御する方法がないことです。 整数と文字列を同じコレクションに追加するのは、それが意図されたものでない可能性があっても、完全に認められています。 そのため、コードをタイプ セーフにするには、コレクションから取得される型が想定どおりであることをチェックする必要があります。

次のコード例では、ジェネリック前の .NET Framework コレクションの 2 つの主な欠点を示します。

```cpp
// perf_pre_generics.cpp
// compile with: /clr

using namespace System;
using namespace System::Collections;

int main()
{
    // This Stack can contain any type.
    Stack ^s = gcnew Stack();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);

    // Push a String to the same Stack.
    // The Stack now contains two different data types.
    s->Push("Seven");

    // Pop the items off the Stack.
    // The item is returned as an Object, so a cast is
    // necessary to convert it to its proper type.
    while (s->Count> 0)
    {
        Object ^o = s->Pop();
        if (o->GetType() == Type::GetType("System.String"))
        {
            Console::WriteLine("Popped a String: {0}", (String ^)o);
        }
        else if (o->GetType() == Type::GetType("System.Int32"))
        {
            Console::WriteLine("Popped an int: {0}", (int)o);
        }
        else
        {
            Console::WriteLine("Popped an unknown type!");
        }
    }
}
```

```Output
Popped a String: Seven
Popped an int: 7
```

## <a name="example"></a>例

新しい <xref:System.Collections.Generic?displayProperty=fullName> 名前空間には <xref:System.Collections?displayProperty=fullName> 名前空間と同じコレクションの多くが含まれていますが、それらはジェネリック型パラメーターを受け入れるように変更されています。 これにより、値型のボックス化とボックス化解除およびコレクションに格納される型の指定不可という非ジェネリック コレクションの 2 つの欠点が取り除かれます。 この 2 つのコレクションに対する操作は同じです。インスタンス化方法のみが異なります。

前述の例を、ジェネリック <xref:System.Collections.Generic.Stack%601> コレクションを使用する次の例と比較してください。 頻繁にアクセスされる大規模なコレクションでは、この例のパフォーマンスは、前の例よりも大幅に高くなります。

```cpp
// perf_post_generics.cpp
// compile with: /clr

#using <System.dll>

using namespace System;
using namespace System::Collections::Generic;

int main()
{
    // This Stack can only contain integers.
    Stack<int> ^s = gcnew Stack<int>();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);
    s->Push(14);

    // You can no longer push a String to the same Stack.
    // This will result in compile time error C2664.
    //s->Push("Seven");

    // Pop an item off the Stack.
    // The item is returned as the type of the collection, so no
    // casting is necessary and no unboxing is performed for
    // value types.
    int i = s->Pop();
    Console::WriteLine(i);

    // You can no longer retrieve a String from the Stack.
    // This will result in compile time error C2440.
    //String ^str = s->Pop();
}
```

```Output
14
```

## <a name="see-also"></a>関連項目

[ジェネリック](generics-cpp-component-extensions.md)