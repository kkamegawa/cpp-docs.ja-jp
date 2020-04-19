---
title: alignment_of クラス
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: d241848edf57fe4876c35e22f1762abf5d6888fa
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302316"
---
# <a name="alignment_of-class"></a>alignment_of クラス

指定された型のアラインメントを取得します。 この構造体は、[alignof](../cpp/alignment-cpp-declarations.md) の観点から実装されています。 単にアラインメント値のクエリを実行するだけの場合は、 **alignof**を直接使用してください。 タグ ディスパッチを行うときのように整数定数が必要な場合は、alignment_of を使用します。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>パラメーター

*Ty*\
照会する型。

## <a name="remarks"></a>コメント

型クエリは、型*Ty*のアラインメントの値を保持します。

## <a name="requirements"></a>要件

**ヘッダー:** \<type_traits >

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[aligned_storage クラス](../standard-library/aligned-storage-class.md)
