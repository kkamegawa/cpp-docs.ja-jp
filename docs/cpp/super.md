---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: a69d177bb83ce404a18d50c8f966be5d81f5fa72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330532"
---
# <a name="super"></a>__super

**Microsoft 固有の仕様**

オーバーライドする関数について、基底クラス実装を呼び出すことを明示できます。

## <a name="syntax"></a>構文

```
__super::member_function();
```

## <a name="remarks"></a>Remarks

オーバーロード解決フェーズ時にすべてのアクセス可能な基底クラス メソッドが考慮され、最優先の一致を示す関数が呼び出されます。

**_ _super**メンバー関数の本体でのみ表示できます。

**_ _super**を使用してでは使用できません宣言します。 参照してください[宣言を使用して](../cpp/using-declaration.md)詳細についてはします。

導入に伴い[属性](../windows/attributes/attributes-alphabetical-reference.md)コードを挿入する、コードには、名前がわからないに呼び出すメソッドを含む 1 つまたは複数の基底クラスが含まれます。

## <a name="example"></a>例

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)