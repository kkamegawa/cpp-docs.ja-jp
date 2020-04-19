---
title: _AtlCreateWndData 構造体
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: d6e3168b5c86de5bce3c3b9d3b0fbdea28ae604f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261243"
---
# <a name="_atlcreatewnddata-structure"></a>_AtlCreateWndData 構造体

この構造体には、ATL でウィンドウ作成コードのクラス インスタンスのデータが含まれています。

## <a name="syntax"></a>構文

```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>メンバー

`m_pThis`<br/>
**this**ポインターをウィンドウ プロシージャで、クラスのインスタンスへのアクセスを取得するために使用します。

`m_dwThreadID`<br/>
現在のクラス インスタンスのスレッド ID。

`m_pNext`<br/>
次へのポインター`_AtlCreateWndData`オブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="see-also"></a>関連項目

[クラスと構造体](../../atl/reference/atl-classes.md)
