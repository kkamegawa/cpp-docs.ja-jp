---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154969"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Microsoft 固有の仕様**

カプセル化されたインターフェイス ポインターを抽出して返します。

## <a name="syntax"></a>構文

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Remarks

抽出し、カプセル化されたインターフェイス ポインターを返しますを NULL にカプセル化されたポインター ストレージをクリアします。 これによって、カプセル化からインターフェイス ポインターが削除されます。 呼び出すかどうかは`Release`返されたインターフェイス ポインター。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)