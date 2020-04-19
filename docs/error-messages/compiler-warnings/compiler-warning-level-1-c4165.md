---
title: コンパイラの警告 (レベル 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: 4d6377730e262efafb38f5e714989e9075a77a04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391739"
---
# <a name="compiler-warning-level-1-c4165"></a>コンパイラの警告 (レベル 1) C4165

'HRESULT' は 'bool'; に変換されます。本当にこれが望ましいこと?

HRESULT を使用する場合、[場合](../../cpp/if-else-statement-cpp.md)ステートメントでは、HRESULT に変換されますが、 [bool](../../cpp/bool-cpp.md) HRESULT として変数を明示的にテストする場合を除き、します。 既定では、この警告はオフに設定されています。

## <a name="example"></a>例

次のサンプルの生成 C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```