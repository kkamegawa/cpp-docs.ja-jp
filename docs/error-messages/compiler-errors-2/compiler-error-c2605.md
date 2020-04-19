---
title: コンパイラエラー C2605
ms.date: 11/04/2016
f1_keywords:
- C2605
helpviewer_keywords:
- C2605
ms.assetid: a0e6f132-5acf-4e19-b277-ddf196d182bf
ms.openlocfilehash: dfa221500d27e71cdbe1ab581eec346c0f268b66
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737882"
---
# <a name="compiler-error-c2605"></a>コンパイラエラー C2605

'name': このメソッドは、マネージド クラスまたは WinRT クラスで予約されています

内部関数用に、いくつかの名前がコンパイラによって予約されています。  詳細については、「[デストラクターとファイナライザー](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)」を参照してください。

## <a name="example"></a>使用例

次の例では C2605 が生成されます。

```cpp
// C2605.cpp
// compile with: /clr /c
ref class R {
protected:
   void Finalize() {}   // C2605
};
```
