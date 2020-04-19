---
title: コンパイラの警告 (レベル 4) C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: 0a84773f80e15b4e6d3851de768751d1d6dc4b4e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990606"
---
# <a name="compiler-warning-level-4-c4634"></a>コンパイラの警告 (レベル 4) C4634

XML ドキュメント コメント: 適用できません: 理由

XML ドキュメントのタグは、すべての C++ コンストラクトに適用できません。  たとえば、名前空間またはテンプレートにドキュメント コメントを追加できません。

詳細については、「 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C4634 警告が生成されます。

```cpp
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

## <a name="example"></a>使用例

次の例では C4634 警告が生成されます。

```cpp
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```
