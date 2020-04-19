---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: 4d51539d2afbb2fbcc860b6c4d821df119aca418
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393897"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress

**Microsoft 固有の仕様**

既存の文字列を解放し、新しく割り当てられた文字列のアドレスを返します。

## <a name="syntax"></a>構文

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>戻り値

`BSTR` でラップされた `_bstr_t` へのポインター。

## <a name="remarks"></a>Remarks

**GetAddress**すべて影響`_bstr_t`オブジェクトをその共有を`BSTR`します。 1 つ以上`_bstr_t`を共有できる、`BSTR`コピー コンス トラクターを使用して、**演算子 =**。

## <a name="example"></a>例

参照してください[_bstr_t::assign](../cpp/bstr-t-assign.md)の例を使用して、 **GetAddress**します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_bstr_t クラス](../cpp/bstr-t-class.md)