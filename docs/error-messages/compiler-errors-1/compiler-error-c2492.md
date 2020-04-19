---
title: コンパイラ エラー C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: fd52b434f86bdc93124c6005bbf7fadad3cb56b2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757060"
---
# <a name="compiler-error-c2492"></a>コンパイラ エラー C2492

'*variable*': スレッドストレージ存続期間を持つデータは dll インターフェイスを含むことはできません

変数は、[スレッド](../../cpp/thread.md)属性と DLL インターフェイスを使用して宣言されます。 `thread` 変数のアドレスは実行時までわからないため、DLL のインポートまたはエクスポートにリンクすることはできません。

次の例では、C2492 が生成されます。

```cpp
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```
