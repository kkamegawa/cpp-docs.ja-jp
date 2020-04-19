---
title: コンパイラの警告 (レベル 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: f3a6497ae7fc2bb3a73684c9dc76401cf96ca3fa
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991315"
---
# <a name="compiler-warning-level-4-c4268"></a>コンパイラの警告 (レベル 4) C4268

' identifier ': コンパイラで生成された既定のコンストラクターで ' const ' 静的/グローバルデータを初期化しました。オブジェクトには0が設定されます

単純なクラスの**const**グローバルまたは静的インスタンスは、コンパイラによって生成される既定のコンストラクターで初期化されます。

## <a name="example"></a>使用例

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

クラスのこのインスタンスは**const**であるため、`m_data` の値を変更することはできません。
