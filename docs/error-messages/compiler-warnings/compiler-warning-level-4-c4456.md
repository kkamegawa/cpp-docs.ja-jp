---
title: コンパイラの警告 (レベル 4) C4456
ms.date: 11/04/2016
f1_keywords:
- C4456
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
ms.openlocfilehash: 006628721598d838070412c895f64b9a8d3de4e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391505"
---
# <a name="compiler-warning-level-4-c4456"></a>コンパイラの警告 (レベル 4) C4456

> 宣言 '*識別子*' 前のローカル宣言を隠します

宣言*識別子*ローカル スコープで同じ名前の前のローカル宣言の宣言を非表示にします。 この警告を参照するかを把握できます。*識別子*いない以前ローカル、可能性のあるユーザーの意図ができない可能性があります、バージョンのローカルに宣言されたローカル スコープ内に解決します。 この問題を解決するには、その他のローカル名と競合しないローカル変数名を提供するをお勧めします。

## <a name="example"></a>例

次の例では、ループ制御変数のため C4456 が生成されます`int x`し、ローカル変数`double x`で`member_fn`と同じ名前です。 この問題を解決するには、ローカル変数に異なる名前を使用します。

```cpp
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        }
        x += u; // uses local double x
    }
} s;
```
