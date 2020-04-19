---
title: コンパイラ エラー C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 61f23269e0b6ed65a485f11e49e492d2248b8a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378935"
---
# <a name="compiler-error-c2397"></a>コンパイラ エラー C2397

'type_1' から 'type_2' への変換で縮小変換が必要です。

均一な初期化を使用する場合、暗黙的な縮小変換が見つかりました。

C 言語での割り当てと初期化、暗黙的な縮小変換を許可して、C++ ダイヤ、場合でも、多くのコード エラーの原因は、予期しない縮小します。 コードを安全にするために、C++ 標準では、初期化リストで縮小変換が発生したときに、診断メッセージが必要です。 Visual C では、診断は、Visual Studio 2015 で均一な初期化のサポートされている構文の先頭を使用する場合に、コンパイラ エラー C2397 です。 コンパイラが生成する[コンパイラの警告 (レベル 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)リストまたは Visual Studio 2013 でサポートされている集約の初期化の構文を使用する場合。

縮小変換は、ターゲットで変換された値の有効範囲に収まることがわかっている場合に、できることができます。 この場合は、知っている、コンパイラがより。 意図的に縮小変換を行うと場合、静的キャストを使用して明示的なの開発者の意図をください。 それ以外の場合、このエラー メッセージほぼ常に示して、コードにバグがあります。 初期化するオブジェクトの入力を処理するために十分な大きさである型であることを確認して修正できます。

次の例では、C2397 を生成し、その修正方法を示しています。

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```