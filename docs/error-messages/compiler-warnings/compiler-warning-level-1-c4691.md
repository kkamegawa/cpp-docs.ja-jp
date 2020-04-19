---
title: コンパイラの警告 (レベル 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 6124171bb5f257dac1dd972f7943d001fb54c9ca
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051355"
---
# <a name="compiler-warning-level-1-c4691"></a>コンパイラの警告 (レベル 1) C4691

' type ': 参照されている型が参照されていないアセンブリ ' file ' で必要です。現在の翻訳単位で定義されている型が代わりに使用されます

元の型定義を含むメタデータファイルが参照されていないため、コンパイラはローカル型定義を使用しています。

*ファイル*を再構築する場合は、C4691 を無視することも、プラグマ[警告](../../preprocessor/warning.md)を使用して無効にすることもできます。  つまり、ビルドするファイルが、コンパイラが型定義を検索するファイルと同じである場合は、C4691 を無視できます。

ただし、メタデータで参照されているアセンブリとは異なる定義をコンパイラが使用すると、予期しない動作が発生する可能性があります。CLR 型は、型の名前だけでなく、アセンブリによっても型指定されます。  つまり、アセンブリ z .dll からの型 Z は、アセンブリ y .dll の型 Z とは異なります。

## <a name="example"></a>例

このサンプルには、元の型定義が含まれています。

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>例

このサンプルでは C4691_a .dll を参照し、Original_Type 型のフィールドを宣言します。

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>例

次の例では、C4691 が生成されます。  このサンプルには Original_Type の定義が含まれており、C4691a を参照していないことに注意してください。

解決するには、元の型定義を含むメタデータファイルを参照し、ローカルの宣言と定義を削除します。

```cpp
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```