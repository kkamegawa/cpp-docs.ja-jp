---
title: コンパイラの警告 (レベル 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 988c1fcbe0826582dceaa527811c688711fd8906
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391843"
---
# <a name="compiler-warning-level-1-c4160"></a>コンパイラの警告 (レベル 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>pragma (pop、...): 以前にプッシュされた識別子が見つかりませんでした '*識別子*'

## <a name="remarks"></a>Remarks

ソース コードのプラグマ ステートメントで、プッシュされていない識別子のポップを試みています。 この警告を回避するには、ポップされている識別子が正しくプッシュされていることを確認してください。

## <a name="example"></a>例

次の例では、C4160 を生成し、その修正方法を示しています。

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```