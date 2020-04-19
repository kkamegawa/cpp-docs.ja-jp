---
title: コンパイラの警告 (レベル 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: cdc25155aced50331851e9581c346155c6f8e45c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966339"
---
# <a name="compiler-warning-level-1-c4407"></a>コンパイラの警告 (レベル 1) C4407

異なるポインター間でメンバー表現がキャストされると、コンパイラが正しくないコードを生成する可能性があります

正しくないキャストが検出されました。

C4407 は、Visual Studio 2005 で実行されたコンパイラ準拠作業のために生成されます。 Pointer-to-member には、修飾名とアドレス演算子 (&) が必要になりました。

C4407 は、多重継承 pointer-to-member を単一継承 pointer-to-member にキャストすると発生する可能性があります。 これが機能する場合もありますが、単一継承の pointer-to-member 表現が十分な情報を保持していないことが原因である場合があります。 **/Vmm**を使用してコンパイルすると解決する場合があります (詳細については、「 [/vmm、/Vmv (General Purpose 表現)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)」を参照してください)。 また、基底クラスを再配置することもできます。基底クラスが派生したからの0以外のオフセットにあるため、コンパイラは変換の情報が失われていることを検出しています。

次の例では、C4407 が生成されます。

```cpp
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```