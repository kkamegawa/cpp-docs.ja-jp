---
title: _bstr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: cc8284bd-f68b-4fff-b2e6-ce8354dabf8b
ms.openlocfilehash: 51561c6f7cf5ba49c86f818d925db548438b2981
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386175"
---
# <a name="_bstr_tdetach"></a>_bstr_t::Detach

**Microsoft 固有の仕様**

`BSTR` でラップされた `_bstr_t` を返し、`BSTR` から `_bstr_t` をデタッチします。

## <a name="syntax"></a>構文

```
BSTR Detach( ) throw;
```

## <a name="return-value"></a>戻り値

`BSTR` によってラップされる `_bstr_t`。

## <a name="example"></a>例

参照してください[_bstr_t::assign](../cpp/bstr-t-assign.md)の例を使用して、**Detach**します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_bstr_t クラス](../cpp/bstr-t-class.md)