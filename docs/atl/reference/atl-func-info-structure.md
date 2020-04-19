---
title: _ATL_FUNC_INFO 構造体
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: f6cf32bab86d741f3b0750c150c7bbc647b27ddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248694"
---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO 構造体

ディスパッチ インターフェイスでメソッドまたはプロパティを記述するために使用する型情報が含まれています。

## <a name="syntax"></a>構文

```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>メンバー

`cc`<br/>
呼び出し規則 この構造体を使用する場合、 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)クラスでは、このメンバーは CC_STDCALL である必要があります。 `CC_CDECL` Windows CE でサポートされている唯一のオプションは、`CALLCONV`のフィールド、`_ATL_FUNC_INFO`構造体。 その他の値はサポートされていませんので、動作が定義されていません。

`vtReturn`<br/>
関数のバリアント型は、値を返します。

`nParams`<br/>
関数のパラメーターの数。

`pVarTypes`<br/>
関数のパラメーターのバリアント型の配列。

## <a name="remarks"></a>Remarks

内部的には、ATL は、タイプ ライブラリから取得した情報を保持するためにこの構造体を使用します。 型情報を使用するイベント ハンドラーを指定する場合は、この構造体を直接操作する必要があります、 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)クラスと[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)マクロ。

## <a name="example"></a>例

IDL で定義されたディスパッチ インターフェイス メソッドを指定します。

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

定義して、`_ATL_FUNC_INFO`構造体。

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>必要条件

ヘッダー: atlcom.h

## <a name="see-also"></a>関連項目

[クラスと構造体](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl クラス](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
