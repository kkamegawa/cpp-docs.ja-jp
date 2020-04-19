---
title: コンパイラ エラー C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: ccd007bf193bd6529748004a96745fafcb9f3226
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447832"
---
# <a name="compiler-error-c2797"></a>コンパイラ エラー C2797

(廃止)メンバー初期化子リストまたは非静的データ メンバー初期化子の内部リストの初期化は実装されていません。

この警告は、Visual Studio 2015 で廃止されています。 Visual Studio 2013 および以前のバージョンでは、Microsoft でC++コンパイラはメンバーの初期化子リストまたは非静的データ メンバー初期化子のいずれかの内部リストの初期化を実装していません。 Visual Studio 2013 Update 3 より前は、これはサイレントに関数呼び出しに変換され、これにより、不適切なコードが生成される可能性がありました。 Visual Studio 2013 Update 3 ではこのことがエラーとして報告されます。

この例では、C2797 が生成されます。

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};
```

また、この例では C2797 も生成されます。

```
struct S1 {
    int i;
};

struct S2 {
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664
    S1 s1;
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664
};
```

この問題を解決するには、内部リストの明示的な構築を使用できます。 例:

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

リストの初期化が必要ない場合:

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

(Visual Studio 2013 Update 3 より前は、Visual Studio 2013 の コンパイラによって暗黙的にこのことが行われました。)