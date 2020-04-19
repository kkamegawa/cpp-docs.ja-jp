---
title: _ATL_MODULE70 構造体
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: d05683383fab64f027f198d49bfbf42aa593d582
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260923"
---
# <a name="atlmodule70-structure"></a>_ATL_MODULE70 構造体

すべての ATL モジュールによって使用されるデータが含まれています。

## <a name="syntax"></a>構文

```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>メンバー

`cbSize`<br/>
バージョン管理に使用される、構造のサイズ。

`m_nLockCnt`<br/>
どのくらいの期間、モジュールをアライブに維持を決定する、参照がカウントされます。

`m_pTermFuncs`<br/>
ATL をシャット ダウン時に呼び出される登録されている関数をトラックします。

`m_csStaticDataInitAndTypeInfo`<br/>
マルチ スレッドの状況での内部データへのアクセスを調整するために使用します。

## <a name="remarks"></a>Remarks

[_ATL_MODULE](atl-typedefs.md#_atl_module)の typedef として定義されて`_ATL_MODULE70`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="see-also"></a>関連項目

[クラスと構造体](../../atl/reference/atl-classes.md)
