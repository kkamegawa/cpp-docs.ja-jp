---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 1cbe88a80b83caa78972d1e2799c1e0d87d1cb0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244529"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>構文

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Remarks

**protected**キーワードをクラス メンバーへのアクセスを指定します、*メンバー リスト*まで、次のアクセス指定子 (**public**または**private**) またはクラス定義の末尾。 として宣言されたクラス メンバー**protected**次でのみ使用できます。

- これらのメンバーを最初に宣言したクラスのメンバー関数。

- これらのメンバーを最初に宣言したクラスのフレンド。

- これらのメンバーを最初に宣言したクラスからパブリックまたはプロテクトのアクセス レベルで派生したクラス。

- プロテクト メンバーへのプライベート アクセスもできる、プライベートとして設定した直接派生クラス。

基底クラスの名前、**protected**キーワードは、基底クラスのパブリックおよびプロテクト メンバーがその派生クラスのプロテクト メンバーを指定します。

プロテクト メンバーがほどプライベートでない**private**宣言されているが、としては、パブリックでないクラスのメンバーにのみアクセスできるメンバー**public**でアクセスできるメンバー任意の関数。

プロテクト メンバーとしても宣言されている**static**は派生クラスのフレンドまたはメンバー関数にアクセスできます。 プロテクト メンバーとして宣言されていない**static**フレンドおよびメンバー関数へのポインター、参照、または派生クラスのオブジェクトからのみ派生クラス内からアクセスできます。

関連情報については、次を参照してください[フレンド](../cpp/friend-cpp.md)、[パブリック](../cpp/public-cpp.md)、[プライベート](../cpp/private-cpp.md)、とでメンバー アクセス テーブル[クラス メンバーへのアクセスの制御](member-access-control-cpp.md).

## <a name="clr-specific"></a>/clr 固有

CLR 型では、C++ アクセス指定子のキーワード (**public**、**private**、および**protected**) 型およびアセンブリに関連メソッドの可視性に影響を与えることができます。 詳細については、次を参照してください。[メンバー アクセス コントロール](member-access-control-cpp.md)します。

> [!NOTE]
>  ファイルがコンパイルされた[/LN](../build/reference/ln-create-msil-module.md)この動作の影響は受けません。 この場合、すべてのマネージド クラス (パブリックかプライベート) が表示されます。

## <a name="end-clr-specific"></a>END /clr 固有

## <a name="example"></a>例

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>関連項目

[クラス メンバーへのアクセス制御](member-access-control-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)