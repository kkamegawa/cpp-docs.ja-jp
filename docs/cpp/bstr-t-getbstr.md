---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: cea3404e0732cb0e16b3fa9199ce95e3dfcc23f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386149"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR

**Microsoft 固有の仕様**

`BSTR` でラップされた `_bstr_t` の先頭を指します。

## <a name="syntax"></a>構文

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>戻り値

`BSTR` でラップされた `_bstr_t` の先頭。

## <a name="remarks"></a>Remarks

**GetBSTR**すべて影響`_bstr_t`オブジェクトをその共有を`BSTR`します。 1 つ以上`_bstr_t`を共有できる、`BSTR`コピー コンス トラクターを使用して、**演算子 =**。

## <a name="example"></a>例

参照してください[_bstr_t::assign](../cpp/bstr-t-assign.md)使用例について**GetBSTR**します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_bstr_t クラス](../cpp/bstr-t-class.md)