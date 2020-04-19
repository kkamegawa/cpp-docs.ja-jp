---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 7408b5c174f76673b56caffd56aaa87895bd08d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154943"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef

**Microsoft 固有の仕様**

呼び出し、`AddRef`のメンバー関数`IUnknown`カプセル化されたインターフェイス ポインター。

## <a name="syntax"></a>構文

```
void AddRef( );
```

## <a name="remarks"></a>Remarks

呼び出し`IUnknown::AddRef`、カプセル化されたインターフェイス ポインターで発生させる、`E_POINTER`ポインターが NULL の場合のエラー。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)