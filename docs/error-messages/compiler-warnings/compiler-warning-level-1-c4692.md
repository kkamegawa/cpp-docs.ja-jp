---
title: コンパイラの警告 (レベル 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: e7ec657956c72f1e321227d54b796164292f0c0e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052487"
---
# <a name="compiler-warning-level-1-c4692"></a>コンパイラの警告 (レベル 1) C4692

'関数': 公開されたメンバーのシグネチャはアセンブリ プライベート ネイティブ型 'native_type' を含んでいます

アセンブリの外部で参照できる型に、アセンブリの外部で参照できないネイティブ型をシグネチャに含むメンバー関数が含まれています。 このため、そのメンバー関数は、それに含まれる型がアセンブリの外部でインスタンス化されている場合は呼び出すことができません。

詳細については、「[型の可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)」を参照してください。

既定では、この警告はオフに設定されています。 詳細については、「 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4692 が生成されます。

```cpp
// C4692.cpp
// compile with: /W1 /c /clr
#pragma warning(default:4692)
class Private_Native_Class {};
public class Public_Native_Class {};
public ref class Public_Ref_Class {
public:
   void Test(Private_Native_Class *) {}   // C4692
   void Test2(Public_Native_Class *) {}   // OK
};
```