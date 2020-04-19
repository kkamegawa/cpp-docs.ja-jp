---
title: クラスと構造体 (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: a37a23296159de2632f6a218eb81315ee2d6a646
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222512"
---
# <a name="classes-and-structs-c"></a>クラスと構造体 (C++)

このセクションでは、C++ のクラスおよび構造体について説明します。 C++ においてこれらの 2 つのコンストラクトは、構造体では既定のアクセシビリティが "public" であるのに対してクラスでは "private" である点を除けば同じです。

クラスと構造体は、独自の型を定義するためのコンストラクトです。 クラスと構造体は、どちらもデータ メンバーとメンバー関数を含めることができ、これらを使用して型の状態や動作を説明できます。

ここでは、次のトピックについて説明します。

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [クラス メンバーの概要](../cpp/class-member-overview.md)

- [メンバー アクセス コントロール](../cpp/member-access-control-cpp.md)

- [継承](../cpp/inheritance-cpp.md)

- [静的メンバー](../cpp/static-members-cpp.md)

- [ユーザー定義型の変換](../cpp/user-defined-type-conversions-cpp.md)

- [変更可能なデータ メンバー (変更可能な指定子)](../cpp/mutable-data-members-cpp.md)

- [入れ子にされたクラス宣言](../cpp/nested-class-declarations.md)

- [匿名クラス型](../cpp/anonymous-class-types.md)

- [メンバーへのポインター](../cpp/pointers-to-members.md)

- [this ポインター](../cpp/this-pointer.md)

- [C++ ビット フィールド](../cpp/cpp-bit-fields.md)

3 つのクラス型は、構造体、クラス、および共用体です。 使用して宣言されている、[構造体](../cpp/struct-cpp.md)、[クラス](../cpp/class-cpp.md)、および[共用体](../cpp/unions.md)キーワード。 次の表は、3 つのクラス型の違いを示しています。

共用体の詳細については、次を参照してください。[共用体](../cpp/unions.md)します。 クラスと c++ 構造体について/cli および C++/cli CX を参照してください[クラスと構造体](../extensions/classes-and-structs-cpp-component-extensions.md)します。

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>構造体、クラス、および共用体のアクセス制御と制約

|構造体|クラス|Unions|
|----------------|-------------|------------|
|クラス キーは**struct**|クラス キーは**class**|クラス キーは**union**|
|既定のアクセスは public|既定のアクセスは private|既定のアクセスは public|
|使用制約なし|使用制約なし|同時に複数のメンバーを使用することはできない|

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)