---
title: コンパイラ エラー C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 19b9c5a54bf405114bd4d596c2a2cc4708aadcc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386792"
---
# <a name="compiler-error-c2712"></a>コンパイラ エラー C2712

> オブジェクト アンワインディングが必要な関数内で __try を使用できません。

## <a name="remarks"></a>Remarks

使用する場合、エラー C2712 が発生する可能性が[/EHsc](../../build/reference/eh-exception-handling-model.md)、構造化例外処理も持つ関数にアンワインディング (破棄) を必要とするオブジェクトとします。

考えられる解決策:

- SEH を必要とするコードを別の関数に移動します。

- デストラクターを含むローカル変数とパラメーターを使用しないように、SEH を使用する関数を記述し直します。 コンストラクターまたはデストラクターで SEH を使用しないようにします。

- /EHsc を使用せずにコンパイルします。

使用して宣言されたメソッドを呼び出す場合もエラー C2712 が発生、 [_ _event](../../cpp/event.md)キーワード。 コンパイラが、基になるイベント オブジェクトの操作を防止し、SEH で生成されたコードを囲むコードを生成するイベントは、マルチ スレッド環境で使用される可能性があります、ため[try-finally ステートメント](../../cpp/try-finally-statement.md)します。 その結果、イベント メソッドを呼び出し、型にデストラクターが含まれる引数を値渡しで渡すと、エラー C2712 が発生します。 このような場合の解決策の 1 つとして、引数を定数参照として渡します。

使用してコンパイルする場合も C2712 が発生 **/clr: 純粋な**でポインターは関数への静的配列を宣言し、`__try`ブロックします。 静的メンバーには、動的な初期化を使用するコンパイラが必要です。 **/clr: 純粋な**、C++ 例外処理することを意味します。 しかし、`__try` ブロックでは C++ の例外処理を実行できません。

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

## <a name="example"></a>例

次の例では、C2712 を生成し、その修正方法を示しています。

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```