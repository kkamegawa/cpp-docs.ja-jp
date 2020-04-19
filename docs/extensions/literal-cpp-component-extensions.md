---
title: literal (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: c0de82d0d1d102f02ea79a4245f2e393439f2e0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515677"
---
# <a name="literal-ccli-and-ccx"></a>literal (C++/CLI および C++/CX)

**/clr** のコンパイルで **literal** としてマークされた変数 (データ メンバー) は、**static const** 変数のネイティブの同等物です。

## <a name="all-platforms"></a>すべてのプラットフォーム

### <a name="remarks"></a>解説

(この言語機能にはランタイムに適用される特記事項がありません。)

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="remarks"></a>解説

(この言語機能には Windows ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

## <a name="remarks"></a>解説

**literal** とマークされたデータ メンバーは宣言時に初期化される必要があり、値は constant integral、enum、または string 型である必要があります。 初期化式の型から static const 型のデータ メンバーへの変換では、ユーザー定義の変換は必要ありません。

実行時に literal フィールドにメモリは割り当てられません。コンパイラは、その値をクラスのメタデータに挿入するだけです。

**static const** とマークされた変数は、他のコンパイラへのメタデータでは利用できません。

詳細については、[static](../cpp/storage-classes-cpp.md) と [const](../cpp/const-cpp.md) を参照してください。

**literal** は状況依存キーワードです。 詳細については、「[状況依存キーワード](context-sensitive-keywords-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>例

次の例は、**literal** 変数が**静的**であることを示しています。

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

## <a name="example"></a>例

次の例は、メタデータでの literal の効果を示しています。

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

メタデータでの `sc` と `lit` の違いに注目してください。`sc` には `modopt` ディレクティブが 適用され、他のコンパイラでは無視される可能性があることを意味します。

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>例

C# で作成された次の例は、前の例で作成されたメタデータを参照し、**literal** 変数と **static const** 変数の効果を示しています。

```cs
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)