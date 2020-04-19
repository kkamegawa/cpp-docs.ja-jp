---
title: コンパイラ エラー C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368033"
---
# <a name="compiler-error-c2461"></a>コンパイラ エラー C2461

> '*クラス*': コンス トラクター構文の正式なパラメーターがありません

クラスのコンス トラクターは、仮パラメーターを指定しません。 コンス トラクターの宣言には、仮パラメーター リストを指定する必要があります。 一覧を空にすることができます。

この問題を解決するには、宣言の後に 1 組のかっこを追加*クラス*:: **クラス*します。

## <a name="example"></a>例

次の例では、C2461 を修正する方法を示します。

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```