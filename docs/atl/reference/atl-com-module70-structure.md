---
title: _ATL_COM_MODULE70 構造体
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c6361fc5374ed732cd9ccbfbbd1d3d1c2fc8f1f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261040"
---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 構造体

ATL で COM に関連するコードで使用されます。

## <a name="syntax"></a>構文

```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>メンバー

`cbSize`<br/>
バージョン管理に使用される、構造のサイズ。

`m_hInstTypeLib`<br/>
このモジュールのタイプ ライブラリへのハンドルのインスタンス。

`m_ppAutoObjMapFirst`<br/>
このモジュールのオブジェクトのマップ エントリの先頭を示す、配列要素のアドレス。

`m_ppAutoObjMapLast`<br/>
このモジュールのオブジェクトのマップ エントリの終了を示す、配列要素のアドレス。

`m_csObjMap`<br/>
オブジェクトのマップ エントリへのアクセスをシリアル化するクリティカル セクション。 ATL で内部的に使用

## <a name="remarks"></a>Remarks

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) _ATL_COM_MODULE70 の typedef として定義されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="see-also"></a>関連項目

[クラスと構造体](../../atl/reference/atl-classes.md)
