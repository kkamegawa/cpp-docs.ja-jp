---
title: コンパイラ エラー C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: dca91b9359417b8c4cce9329e2aa25107016c086
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750001"
---
# <a name="compiler-error-c3101"></a>コンパイラ エラー C3101

名前付き属性の引数 ' field ' に対して無効な式です

名前付き属性の引数を初期化する場合、値はコンパイル時の定数である必要があります。

属性の詳細については、「[ユーザー定義の属性](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3101 が生成されます。

```cpp
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```
