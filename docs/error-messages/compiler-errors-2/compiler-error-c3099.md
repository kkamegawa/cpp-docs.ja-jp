---
title: コンパイラ エラー C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 81f508c47c678d86f8f95303861b42f8a70daa57
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750053"
---
# <a name="compiler-error-c3099"></a>コンパイラ エラー C3099

'keyword': マネージド属性には [System::AttributeUsageAttribute] を使用してください。WinRT 属性には [Windows::Foundation::Metadata::AttributeUsageAttribute] を使用してください。

**/Clr**属性を宣言するには <xref:System.AttributeUsageAttribute> を使用します。 `Windows::Foundation::Metadata::AttributeUsageAttribute` を使用して、Windows ランタイム属性を宣言します。

/CLR 属性の詳細については、「[ユーザー定義の属性](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。 Windows ランタイムでサポートされる属性については、「 [Windows. Foundation. Metadata 名前空間](/uwp/api/windows.foundation.metadata)」を参照してください。

## <a name="example"></a>使用例

次の例では C3099 を生成し、その修正方法を示しています。

```cpp
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```
