---
title: コンパイラの警告 (レベル 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: bcd51c66359d0553b7657d85f5b45ee22d4648ff
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991651"
---
# <a name="compiler-warning-level-4-c4100"></a>コンパイラの警告 (レベル 4) C4100

'identifier' : 未参照仮パラメーター

仮パラメーターが関数の本体で参照されていません。 未参照のパラメーターは無視されます。

また、コードがプリミティブ型の他の未参照パラメーターでデストラクターを呼び出すと C4100 が出される可能性があります。  これは、Microsoft C++コンパイラの制限事項です。

次の例では、C4100 が生成されます。

```cpp
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```
