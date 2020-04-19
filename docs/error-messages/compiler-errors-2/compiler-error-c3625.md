---
title: コンパイラ エラー C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: 83b6756c75f90380024a8f31df62290bed1f7738
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761908"
---
# <a name="compiler-error-c3625"></a>コンパイラ エラー C3625

'native_type': ネイティブ型はマネージド型または WinRT 型の 'type' から派生することはできません

マネージド クラスまたは WinRT クラスからネイティブ クラスを継承できません。 詳細については、「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では警告 C3625 が生成されます。

```cpp
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
