---
title: コンパイラの警告 (レベル 4) C4625
ms.date: 11/04/2016
f1_keywords:
- C4625
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
ms.openlocfilehash: d98e295a9a48da16b58202bc172e112b5c0287d9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990714"
---
# <a name="compiler-warning-level-4-c4625"></a>コンパイラの警告 (レベル 4) C4625

'derived class': 基底クラスのコピー コンストラクターがアクセスできないか削除されているため、コピー コンストラクターは暗黙的に削除済みとして定義されました

コピー コンストラクターは基底クラスで削除されているかアクセスできないため、派生クラスでは生成されません。 この型のオブジェクトをコピーしようとすると、コンパイラ エラーが発生します。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では C4625 が生成され、その修正方法が示されています。

```cpp
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```
