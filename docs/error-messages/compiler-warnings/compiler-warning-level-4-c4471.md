---
title: コンパイラの警告 (レベル 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 0345b730b8fc37329f632bb5d8486c67efd8e3b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400787"
---
# <a name="compiler-warning-level-4-c4471"></a>コンパイラの警告 (レベル 4) C4471

'*列挙*': スコープを持たない列挙型の事前宣言は、基になる型 (int が想定されます) をいる必要があります

スコープを持たない列挙型の事前宣言を基になる型の指定子がありませんでした。 既定では、Visual C が前提としています`int`は列挙体の基になる型です。 これは別の種類はたとえば、この列挙型の定義で使用さまざまな明示的な型が指定されている場合がある場合、または別の型が暗黙的に初期化子によって設定されている場合、問題が発生することができます。 移植性の問題があります。他のコンパイラと見なさないでください`int`列挙体の基になる型です。

この警告は既定ではオフです。/Wall または/w を使用する*N*、コマンドラインで有効にまたは #pragma 4471[警告](../../preprocessor/warning.md)ソース ファイル内です。

場合によっては、この警告は誤ったです。 定義の後に事前宣言列挙型の場合、この警告が起動されることがあります。 たとえば、このコードは、場合でも、C4471 を引き起こす可能性が有効では。

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>例

一般に、事前宣言ではなくスコープを持たない列挙型の完全な定義を使用しても安全です。 ヘッダー ファイルで、定義を配置し、それを参照するソース ファイルに含めることできます。 これは、c++ 98 以降に記述されたコードでは動作します。 このソリューションの移植性と保守のしやすさをお勧めします。

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>例

C++ 11 では、スコープを持たない列挙型にし、その前方宣言に、明示的な型を追加できます。 このソリューションは、複雑なヘッダーの信頼ロジック事前宣言ではなく、定義の使用を防止する場合にのみお勧めします。 このソリューションは、保守の問題につながることができます: 列挙型の定義に使用される基になる型を変更すると、すべての一致する、事前宣言を変更する必要がありますまたはサイレント エラーは、コードにする必要があります。 事前宣言は、この問題を最小限に抑えるヘッダー ファイルに配置できます。

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

列挙体は、明示的な型を指定する場合を警告を有効にもお勧め[C4369](compiler-warning-level-1-C4369.md)既定でオンになっています。 列挙項目が明示的に指定された型よりも別の種類に必要な場合を識別します。

## <a name="example"></a>例

スコープを持つ列挙型、c++ 11 で新たに導入された機能を使用するコードを変更することができます。 スコープ列挙型を使用する、定義と列挙型を使用するクライアント コードの両方を変更する必要があります。 使用する、スコープ列挙型、名前空間の汚染の問題がある場合に定義された列挙項目の名前は、列挙型のスコープに限定することをお勧めします。 スコープ列挙型の別の機能では、そのメンバーを暗黙的にもう 1 つ整数型または列挙型、微妙なバグの原因となる可能性に変換できません。

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```

