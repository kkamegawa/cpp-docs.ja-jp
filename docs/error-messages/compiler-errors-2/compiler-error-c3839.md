---
title: コンパイラ エラー C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 19a1055a461d76856cc3bccbd9f8af0f0dcff356
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754928"
---
# <a name="compiler-error-c3839"></a>コンパイラ エラー C3839

マネージド型または WinRT 型で配置を変更することはできません

マネージ型または Windows ランタイム型の変数のアラインメントは CLR または Windows ランタイムによって制御され、 [align](../../cpp/align-cpp.md)を使用して変更することはできません。

次の例では C3839 が生成されます。

```cpp
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```
