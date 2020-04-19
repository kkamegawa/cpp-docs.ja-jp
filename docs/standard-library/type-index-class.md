---
title: type_index クラス
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: b30c9719957b9ffc5f3ce17692eb90c1b266ae0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447049"
---
# <a name="typeindex-class"></a>type_index クラス

`type_index` クラスは、[type_info クラス](../cpp/type-info-class.md)へのポインターをラップして、このクラスのオブジェクトでインデックスを作成しやすくします。

class type_index { public: type_index(const type_info& tinfo); const char *name() const; size_t hash_code() const; bool operator==(const type_info& right) const; bool operator!=(const type_info& right) const; bool operator<(const type_info& right) const; bool operator\<=(const type_info& right) const; bool operator>(const type_info& right) const; bool operator>=(const type_info& right) const; };

このコンストラクターは、`ptr` を `&tinfo`に初期化します。

`name` は、`ptr->name()` を返します。

`hash_code` の場合、`ptr->hash_code().` が返されます。

`operator==` は、`*ptr == right.ptr` を返します。

`operator!=` は、`!(*this == right)` を返します。

`operator<` は、`*ptr->before(*right.ptr)` を返します。

`operator<=` の場合、`!(right < *this).` が返されます。

`operator>` は、`right < *this` を返します。

`operator>=` は、`!(*this < right)` を返します。

## <a name="see-also"></a>関連項目

[ランタイム型情報](../cpp/run-time-type-information.md)\
[\<typeindex>](../standard-library/typeindex.md)
