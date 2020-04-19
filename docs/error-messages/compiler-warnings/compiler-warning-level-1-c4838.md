---
title: コンパイラの警告 (レベル 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: 552c7d9e868ae531b1ff2ef20db7adfa813a4fbe
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051234"
---
# <a name="compiler-warning-level-1-c4838"></a>コンパイラの警告 (レベル 1) C4838

' type_1 ' から ' type_2 ' への変換には縮小変換が必要です

集計またはリストの初期化を使用しているときに、暗黙的な縮小変換が見つかりました。

C 言語では、割り当てと初期化で暗黙的な縮小変換C++を行うことができます。また、予期しない縮小が多くのコードエラーの原因である場合でも、これに適合します。 コードの安全性を高めるためC++に、初期化リストで縮小変換が発生した場合、標準では診断メッセージが必要になります。 Visual Studio C++2015 以降でサポートされている均一な初期化構文を使用すると、visual Studio 診断は[コンパイラエラー C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)となります。 Visual Studio 2013 でサポートされているリストまたは集計の初期化構文を使用すると、コンパイラによって警告 C4838 が生成されます。

変換された値の範囲がターゲットに適合する可能性があることがわかっている場合は、縮小変換に対応できます。 この場合、コンパイラよりも多くのことがわかっています。 縮小変換を意図的に行う場合は、静的なキャストを使用して意図を明確にしてください。 それ以外の場合、この警告メッセージは、ほとんどの場合、コードにバグがあることを示しています。 この問題を解決するには、初期化するオブジェクトに、入力を処理するのに十分な大きさの型があることを確認します。

次の例では、C4838 を生成し、その修正方法の1つを示しています。

```cpp
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```