---
title: _ATL_WIN_MODULE70 構造体
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 0b636d328852daf821269230aae443cef084578b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260754"
---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 構造体

ATL でウィンドウ作成コードで使用されます。

## <a name="syntax"></a>構文

```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>メンバー

`cbSize`<br/>
バージョン管理に使用される、構造のサイズ。

`m_csWindowCreate`<br/>
ウィンドウの登録コードへのアクセスをシリアル化するために使用します。 ATL で内部的に使用

`m_pCreateWndList`<br/>
Windows をそれらのオブジェクトにバインドするために使用します。 ATL で内部的に使用

`m_rgWindowClassAtoms`<br/>
終了時に正しく登録それらができるように、ウィンドウ クラスの登録を追跡するために使用します。 ATL で内部的に使用

## <a name="remarks"></a>Remarks

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)の typedef として定義されて`_ATL_WIN_MODULE70`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="see-also"></a>関連項目

[クラスと構造体](../../atl/reference/atl-classes.md)
