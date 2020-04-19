---
title: コンパイラの警告 (レベル 3) C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 1e3eab6e96e829e3c3fd9304e757ba653e8f19b4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991818"
---
# <a name="compiler-warning-level-3-c4641"></a>コンパイラの警告 (レベル 3) C4641

XML ドキュメントコメントはあいまいな相互参照を含んでいます

コンパイラは、参照を明確に解決できませんでした。 この警告を解決するには、参照を明確にするために必要なパラメーター情報を指定します。

詳細については、「 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C4641 が生成されます。

```cpp
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```
