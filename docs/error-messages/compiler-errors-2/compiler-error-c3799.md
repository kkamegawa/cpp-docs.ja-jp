---
title: コンパイラ エラー C3799
ms.date: 11/04/2016
f1_keywords:
- C3799
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
ms.openlocfilehash: 19ff414bde9bb24fca62fd10cfef6d18109199e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400124"
---
# <a name="compiler-error-c3799"></a>コンパイラ エラー C3799

インデックス付きプロパティが空のパラメーター リストを含めることはできません。

インデックス付きプロパティの宣言が正しくありません。 詳細については、「[方法 :プロパティを使用してC++/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md)します。

## <a name="example"></a>例

次の例では、C3799 を生成し、その修正方法を示しています。

```cpp
// C3799.cpp
// compile with: /clr /c
ref struct C {
   property int default[] {   // C3799
   // try the following line instead
   // property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};
```