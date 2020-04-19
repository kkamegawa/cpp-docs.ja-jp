---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: cf4cea35386d1f781d6d2946c1730ba2e18dacea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399227"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Microsoft 固有の仕様**

呼び出し、**リリース**のメンバー関数`IUnknown`カプセル化されたインターフェイス ポインター。

## <a name="syntax"></a>構文

```
void Release( );
```

## <a name="remarks"></a>Remarks

呼び出し`IUnknown::Release`、カプセル化されたインターフェイス ポインターで発生させる、`E_POINTER`このインターフェイス ポインターが NULL の場合のエラー。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)