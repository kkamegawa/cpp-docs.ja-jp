---
title: レジストリ データ エクス チェンジに関するマクロ
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: 69b823cbcd85ebaaeb05979283ea4f8fea80f4b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197485"
---
# <a name="registry-data-exchange-macros"></a>レジストリ データ エクス チェンジに関するマクロ

これらのマクロは、レジストリ データの交換操作を実行します。

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|レジストリ データ エクス チェンジ マップの先頭をマークします。|
|[END_RDX_MAP](#end_rdx_map)|レジストリ データ エクス チェンジ map の末尾をマークします。|
|[RDX_BINARY](#rdx_binary)|BYTE 型の指定したメンバー変数で指定されたレジストリ エントリに関連付けます。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|指定されたレジストリ エントリを CString 型の指定したメンバー変数に関連付けます。|
|[RDX_DWORD](#rdx_dword)|指定されたレジストリ エントリを DWORD 型の指定したメンバー変数に関連付けます。|
|[RDX_TEXT](#rdx_text)|TCHAR 型の指定したメンバー変数で指定されたレジストリ エントリに関連付けます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlplus.h

##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP

レジストリ データ エクス チェンジ マップの先頭をマークします。

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Remarks

次のマクロは、システム レジストリにエントリを読み書きするレジストリ データ エクス チェンジ マップ内で使用されます。

|マクロ|説明|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|BYTE 型の指定したメンバー変数で指定されたレジストリ エントリに関連付けます。|
|[RDX_DWORD](#rdx_dword)|指定されたレジストリ エントリを DWORD 型の指定したメンバー変数に関連付けます。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|指定されたレジストリ エントリを CString 型の指定したメンバー変数に関連付けます。|
|[RDX_TEXT](#rdx_text)|TCHAR 型の指定したメンバー変数で指定されたレジストリ エントリに関連付けます。|

グローバル関数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)、か、コードは、システム レジストリの間でデータを交換する必要があるとき、BEGIN_RDX_MAP と END_RDX_MAP マクロによって作成された同じ名前のメンバー関数を使用して、RDX マップで指定する変数。

##  <a name="end_rdx_map"></a>  END_RDX_MAP

レジストリ データ エクス チェンジ map の末尾をマークします。

```
END_RDX_MAP
```

##  <a name="rdx_binary"></a>  RDX_BINARY

BYTE 型の指定したメンバー変数で指定されたレジストリ エントリに関連付けます。

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>パラメーター

*rootkey*<br/>
レジストリ キーのルート。

*サブキー*<br/>
レジストリのサブキー。

*valuename*<br/>
レジストリ キー。

*member*<br/>
指定されたレジストリ エントリに関連付けるメンバー変数です。

*member_size*<br/>
メンバー変数のバイト単位のサイズ。

### <a name="remarks"></a>Remarks

このマクロは、メンバー変数を特定のレジストリ エントリに関連付ける BEGIN_RDX_MAP と END_RDX_MAP マクロと組み合わせて使用します。 グローバル関数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)、BEGIN_RDX_MAP END_RDX_MAP マクロによって作成された同じ名前のメンバー関数は、システム レジストリとメンバー変数の間のデータ交換を実行するために使用する必要がありますかRDX マップします。

##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT

指定されたレジストリ エントリを CString 型の指定したメンバー変数に関連付けます。

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>パラメーター

*rootkey*<br/>
レジストリ キーのルート。

*サブキー*<br/>
レジストリのサブキー。

*valuename*<br/>
レジストリ キー。

*member*<br/>
指定されたレジストリ エントリに関連付けるメンバー変数です。

*member_size*<br/>
メンバー変数のバイト単位のサイズ。

### <a name="remarks"></a>Remarks

このマクロは、メンバー変数を特定のレジストリ エントリに関連付ける BEGIN_RDX_MAP と END_RDX_MAP マクロと組み合わせて使用します。 グローバル関数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)、BEGIN_RDX_MAP END_RDX_MAP マクロによって作成された同じ名前のメンバー関数は、システム レジストリとメンバー変数の間のデータ交換を実行するために使用する必要がありますかRDX マップします。

##  <a name="rdx_dword"></a>  RDX_DWORD

指定されたレジストリ エントリを DWORD 型の指定したメンバー変数に関連付けます。

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>パラメーター

*rootkey*<br/>
レジストリ キーのルート。

*サブキー*<br/>
レジストリのサブキー。

*valuename*<br/>
レジストリ キー。

*member*<br/>
指定されたレジストリ エントリに関連付けるメンバー変数です。

*member_size*<br/>
メンバー変数のバイト単位のサイズ。

### <a name="remarks"></a>Remarks

このマクロは、メンバー変数を特定のレジストリ エントリに関連付ける BEGIN_RDX_MAP と END_RDX_MAP マクロと組み合わせて使用します。 グローバル関数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)、BEGIN_RDX_MAP END_RDX_MAP マクロによって作成された同じ名前のメンバー関数は、システム レジストリとメンバー変数の間のデータ交換を実行するために使用する必要がありますかRDX マップします。

##  <a name="rdx_text"></a>  RDX_TEXT

TCHAR 型の指定したメンバー変数で指定されたレジストリ エントリに関連付けます。

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>パラメーター

*rootkey*<br/>
レジストリ キーのルート。

*サブキー*<br/>
レジストリのサブキー。

*valuename*<br/>
レジストリ キー。

*member*<br/>
指定されたレジストリ エントリに関連付けるメンバー変数です。

*member_size*<br/>
メンバー変数のバイト単位のサイズ。

### <a name="remarks"></a>Remarks

このマクロは、メンバー変数を特定のレジストリ エントリに関連付ける BEGIN_RDX_MAP と END_RDX_MAP マクロと組み合わせて使用します。 グローバル関数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)、BEGIN_RDX_MAP END_RDX_MAP マクロによって作成された同じ名前のメンバー関数は、システム レジストリとメンバー変数の間のデータ交換を実行するために使用する必要がありますかRDX マップします。

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
