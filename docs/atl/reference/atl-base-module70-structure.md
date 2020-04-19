---
title: _ATL_BASE_MODULE70 構造体
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 4fddd4b3af6155d0663b9c01edfab4fcf4a60426
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260988"
---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 構造体

ATL を使用するすべてのプロジェクトで使用されます。

## <a name="syntax"></a>構文

```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```

## <a name="members"></a>メンバー

`cbSize`<br/>
バージョン管理に使用される、構造のサイズ。

`m_hInst`<br/>
`hInstance` (Exe または dll) は、このモジュールにします。

`m_hInstResource`<br/>
既定のインスタンスのリソース ハンドル。

`m_bNT5orWin98`<br/>
オペレーティング システムのバージョン情報。 ATL で内部的に使用

`dwAtlBuildVer`<br/>
ATL のバージョンが格納されます。 Currently 0x0700.

`pguidVer`<br/>
ATL の内部の GUID です。

`m_csResource`<br/>
アクセスを同期するため、`m_rgResourceInstance`配列。 ATL で内部的に使用

`m_rgResourceInstance`<br/>
ATL が対応であるすべてのリソース インスタンス内のリソースの検索に使用する配列。 ATL で内部的に使用

## <a name="remarks"></a>Remarks

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) _ATL_BASE_MODULE70 の typedef として定義されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore.h

## <a name="see-also"></a>関連項目

[クラスと構造体](../../atl/reference/atl-classes.md)
