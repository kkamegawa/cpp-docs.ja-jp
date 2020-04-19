---
title: コンパイラ エラー C3771
ms.date: 11/04/2016
f1_keywords:
- C3771
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
ms.openlocfilehash: 6b15d867bbaf66f511cbda200d692f5db4371ab3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400163"
---
# <a name="compiler-error-c3771"></a>コンパイラ エラー C3771

"identifier" : フレンド宣言が一番近い名前空間スコープに見つかりませんでした

指定したテンプレート *identifier* のクラス テンプレート宣言が、現在の名前空間内に見つかりません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- テンプレート識別子のクラス テンプレート宣言が現在の名前空間で定義されていること、またはテンプレート識別子が完全修飾名であることを確認します。

## <a name="example"></a>例

次のコード例では、名前空間 `NA`でクラス テンプレートと関数を宣言しますが、名前空間 `NB`でフレンド関数テンプレートを宣言しようとします。

```cpp
// C3771.cpp
// compile with: /c

namespace NA {
template<class T> class A {
    void aFunction(T t) {};
    };
}
// using namespace NA;
namespace NB {
    class X {
        template<class T> friend void A<T>::aFunction(T); // C3771
// try the following line instead
//      template<class T> friend void NA::A<T>::aFunction(T);
// or try "using namespace NA;" instead.
    };
}
```

## <a name="see-also"></a>関連項目

[テンプレート](../../cpp/templates-cpp.md)