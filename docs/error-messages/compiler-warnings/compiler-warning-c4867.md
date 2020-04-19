---
title: コンパイラの警告 C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: e093d262bc26cf0acfbb181d621fffc1aa391ee9
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626589"
---
# <a name="compiler-warning-c4867"></a>コンパイラの警告 C4867

' function ': 関数呼び出しに引数リストがありません。メンバーへのポインターを作成するには、' call ' を使用します

メンバー関数へのポインターが正しく初期化されませんでした。

この警告は、Visual Studio 2005 で行われたコンパイラ準拠作業の結果として生成されます。強化された pointer-to-member 準拠。  Visual Studio 2005 より前にコンパイルされたコードでは、C4867 が生成されるようになりました。

この警告は、常にエラーとして表示されます。 この警告を無効にするには、 [warning](../../preprocessor/warning.md) プラグマを使用します。 C4867 と MFC/ATL の詳細については、 [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)を参照してください。

## <a name="example"></a>例

次の例では、C4867 が生成されます。

```cpp
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```