---
title: コンパイラ エラー C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: df0f656c9db23739ec62629088b9cc5f7950a92d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386864"
---
# <a name="compiler-error-c2672"></a>コンパイラ エラー C2672

> '*関数*': 一致するオーバー ロードされた関数が見つかりませんでした

コンパイラは、指定された関数と一致するオーバー ロード関数を見つけられませんでした。 一致するパラメーター、または一致する機能はありませんが、コンテキスト内の必要なユーザー補助を持っている関数は見つかりませんでした。

特定の標準ライブラリ コンテナーまたはアルゴリズムを使用する場合、型はアクセス可能なメンバーまたはコンテナーまたはアルゴリズムの要件を満たすフレンド関数を提供する必要があります。 たとえば、反復子の型の派生元`std::iterator<>`します。 比較操作または要素の種類のコンテナーに他の演算子の使用を左側と右側のオペランドとして、型と見なす必要があります。 右側のオペランドが、型の非メンバー関数として、演算子の実装を必要とするように、型の使用します。

## <a name="example"></a>例

Visual Studio 2017 の前に、コンパイラのバージョンでは、一部のテンプレート コンテキストで修飾名のアクセス確認は実行しませんでした。 これは、名前にアクセスできないために置換が失敗すると予想される場合に、予期される SFINAE の動作に干渉する可能性があります。 コンパイラが演算子の誤ったオーバーロードを誤って呼び出すために、これが原因でクラッシュまたは実行時に予期しない動作が発生する可能性があります。 Visual Studio 2017 年では、コンパイラ エラーが発生します。

この例では、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 でエラーが発生します。 この問題を解決するには、ことをアクセス可能なテンプレート パラメーターのメンバーが評価されます。

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```