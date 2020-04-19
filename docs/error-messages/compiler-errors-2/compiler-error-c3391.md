---
title: コンパイラ エラー C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 7590ba9431892c07a32c27fdc97604c8b005fe33
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912856"
---
# <a name="compiler-error-c3391"></a>コンパイラ エラー C3391

' type_arg ': ジェネリック ' generic_type ' のジェネリックパラメーター ' param ' の型引数が無効です。 null 非許容の値型でなければなりません

ジェネリック型のインスタンス化が正しく行われませんでした。 型定義を確認してください。 詳細については、「<xref:System.Nullable> と[ジェネリック](../../extensions/generics-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例でC#は、を使用して、/cli でC++ジェネリック型を作成するときにサポートされない特定の制約を持つジェネリック型を含むコンポーネントを作成します。 詳細については、「[型パラメーターの制約](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)」を参照してください。

```csharp
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

C3391 コンポーネントが使用可能になると、次の例では C3391 が生成されます。

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```