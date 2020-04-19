---
title: コンパイラの警告 (レベル 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 8567e7392537507a25121977448ac47ec079316b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051375"
---
# <a name="compiler-warning-level-1-c4677"></a>コンパイラの警告 (レベル 1) C4677

' function ': プライベートでないメンバーのシグネチャには、アセンブリプライベート型 ' private_type ' が含まれています

アセンブリの外部でパブリックアクセシビリティを持つ型は、アセンブリ外部のプライベートアクセスを持つ型を使用します。 パブリックアセンブリ型を参照するコンポーネントは、アセンブリプライベート型を参照する型メンバーまたはメンバーを使用できません。

## <a name="example"></a>例

次の例では、C4677 が生成されます。

```cpp
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```