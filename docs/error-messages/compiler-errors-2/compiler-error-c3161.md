---
title: コンパイラエラー C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 7315dad7959cdd3b950ed814b13be3867399d332
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761817"
---
# <a name="compiler-error-c3161"></a>コンパイラエラー C3161

' interface ': インターフェイスでクラス、構造体、共用体、またはインターフェイスを入れ子にすることはできません。クラス、構造体、または共用体にインターフェイスを入れ子にすることは無効です

[__Interface](../../cpp/interface.md)は、グローバルスコープまたは名前空間内でのみ使用できます。 クラス、構造体、または共用体は、インターフェイスには記述できません。

## <a name="example"></a>使用例

次の例では、C3161 が生成されます。

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
