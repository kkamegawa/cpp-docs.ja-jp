---
title: コンパイラの警告 (レベル 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 73143e38b66471a41cc61f818f7618b9ddafcaa1
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966470"
---
# <a name="compiler-warning-level-1-c4376"></a>コンパイラの警告 (レベル 1) C4376

アクセス指定子 'old_specifier:' はサポートされていません。'new_specifier:' を使用してください

メタデータで型とメンバーのアクセシビリティを指定する方法の詳細については、「[方法: クラスと構造体を定義およびC++使用する (/cli)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)」の「[型の可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)と[メンバーの可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)」を参照してください。

## <a name="example"></a>例

次の例では、C4376 が生成されます。

```cpp
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```