---
title: コンパイラの警告 C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: f1f5e5be2606a03ec5e9ecd0c571f94c25f82494
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623745"
---
# <a name="compiler-warning-c4355"></a>コンパイラの警告 C4355

'this' : ベース メンバー初期化リストで使用されました。

**this**ポインターは、非静的メンバー関数内でのみ有効です。 基底クラスの初期化子リストでは使用できません。

基底クラスのコンストラクターとクラスメンバーのコンストラクターは、**this**コンストラクターの前に呼び出されます。 実際には、構築されていないオブジェクトへのポインターを別のコンストラクターに渡しました。 他のコンストラクターがメンバーにアクセスしたり、このでメンバー関数を呼び出したりすると、結果は未定義になります。 すべての構築が完了するまで、**this**ポインターを使用しないでください。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4355 が生成されます。

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```