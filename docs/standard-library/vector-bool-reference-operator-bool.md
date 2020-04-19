---
title: vector&lt;bool&gt;::reference::operator bool
ms.date: 11/04/2016
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
ms.openlocfilehash: ca2d21a7706248cd84ca3591eb717e4081972f9c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452119"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

からブール型への`vector<bool>::reference`暗黙の型変換を提供します。

## <a name="syntax"></a>構文

```cpp
operator bool() const;
```

## <a name="return-value"></a>戻り値

[vector\<bool>](../standard-library/vector-bool-class.md) オブジェクトの要素のブール値。

## <a name="remarks"></a>Remarks

`vector<bool>` オブジェクトはこの演算子では変更できません。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<vector>

**名前空間:** std

## <a name="see-also"></a>関連項目

[vector\<bool>::reference クラス](../standard-library/vector-bool-reference-class.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
