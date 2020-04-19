---
title: is_literal_type クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 450c32d050a18f64e71992bd7a30412ebafe93de
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456221"
---
# <a name="isliteraltype-class"></a>is_literal_type クラス

型を `constexpr` 変数として使用できるか、または `constexpr` 関数で構築、使用、または返すことができるかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型*T*が*リテラル型*である場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 リテラル型は、 **void**、スカラー型、参照型、リテラル型の配列、またはリテラルクラス型のいずれかになります。 リテラル クラス型は、単純なデストラクターを持つクラス型であり、集計の型であるか、または少なくとも 1 つのムーブ禁止、コピー禁止の `constexpr` コンストラクターを持ち、そのすべての基底クラスと非静的データ メンバーは、非 volatile のリテラル型です。 リテラルの型は常にリテラル型ですが、リテラル型の概念は、コンパイラがコンパイル時に `constexpr` として評価できるあらゆるものを含みます。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
