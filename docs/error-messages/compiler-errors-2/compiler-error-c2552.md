---
title: コンパイラ エラー C2552
ms.date: 11/04/2016
f1_keywords:
- C2552
helpviewer_keywords:
- C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
ms.openlocfilehash: 7f3e4cfc46655c5201e7a79a9333f532a8fcab9c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740807"
---
# <a name="compiler-error-c2552"></a>コンパイラ エラー C2552

'identifier': 初期化子リストによる個別の識別子の初期化に誤りがあります

集約識別子は正しく初期化されませんでした。

[集計](../../c-language/initializing-aggregate-types.md)は次のように定義されます。

- 配列

- 次のものがないクラス、構造体、共用体:

   - コンストラクター

   - プライベートまたはプロテクト メンバー

   - 基底クラス

   - 仮想関数

さらに、Visual C++ は、コンストラクターを含む集約のデータ型を許可しません。

型で集約の初期化を試みると、C2552 が発生する場合があります。発生の理由となる状況を次に示します。

- 型に 1 つ以上のユーザー定義のコンストラクターがある場合。

- 型に 1 つ以上の静的ではないプライベート データ メンバーがある場合。

- 型に 1 つ以上の仮想関数がある場合。

- 型に基底クラスがある場合。

- 型が ref クラスまたは CLR インターフェイスである場合。

- 型に、要素にデストラクターを持つ固定されていない次元配列 (ゼロ配列) がある場合。

次の例では警告 C2552 が生成されます。

```cpp
// C2552.cpp
// compile with: /clr
#include <string>
using namespace std;

struct Pair_Incorrect {
private:
   string m_name;
   double m_val;
};

struct Pair_Correct1 {
public:
   Pair_Correct1(string name, double val)
      : m_name(name), m_val(val) {}

private:
   string m_name;
   double m_val;
};

struct Pair_Correct2 {
public:
   string m_name;
   double m_val;
};

int main() {
   // To fix, add a constructor to this class and use it for
   // initializing the data members, see Pair_Correct1 (below)
   // or
   // Do not have any private or protected non-static data members,
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in
   // case your object model requires some non-static data members to
   // be private or protected

   string name("John");
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552

   // initialize a CLR immutable value type that has a constructor
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552

   Pair_Correct1 pair2( name, 0.0 );
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );
   Pair_Correct2 pair4 = { name, 0.0 };
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);
}
```
