---
title: コンパイラの警告 (レベル 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: bd2ecff5adc6538f75c61772b785acbfc89092ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401801"
---
# <a name="compiler-warning-level-3-c4580"></a>コンパイラの警告 (レベル 3) C4580

[attribute] は非推奨とされます。System::Attribute または Platform::Metadata を基底クラスとして指定してください

[[属性](../../windows/attributes/attribute.md)] がユーザー定義の属性を作成するための構文をお勧めします。 詳細については、「 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。 CLR コードの場合は、`System::Attribute` から属性を派生させます。 Windows ランタイム コードの場合は、`Platform::Metadata` から属性を派生させます。

## <a name="example"></a>例

次の例では、C3454 を生成し、その修正方法を示しています。

```cpp
// C4580.cpp
// compile with: /W3 /c /clr
[attribute]   // C4580
public ref class Attr {
public:
   int m_t;
};

public ref class Attr2 : System::Attribute {
public:
   int m_t;
};
```