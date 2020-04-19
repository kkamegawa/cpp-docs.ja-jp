---
title: COM マップマクロ
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 3159a53b5a500aa61b85cf2bc5a97d321ed6ebb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864932"
---
# <a name="com-map-macros"></a>COM マップマクロ

これらのマクロは、COM インターフェイスマップを定義します。

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|COM インターフェイスマップエントリの先頭をマークします。|
|[END_COM_MAP](#end_com_map)|COM インターフェイスマップエントリの終了をマークします。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="begin_com_map"></a>BEGIN_COM_MAP

COM マップは、オブジェクトのインターフェイスを `QueryInterface`を通じてクライアントに公開するメカニズムです。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>パラメーター

*x*<br/>
からインターフェイスを公開するクラスオブジェクトの名前。

### <a name="remarks"></a>解説

[CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)は、COM マップ内のインターフェイスのポインターのみを返します。 BEGIN_COM_MAP マクロを使用してインターフェイスマップを開始し、 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)マクロまたはそのバリアントの1つを使用してインターフェイスのエントリを追加し、 [END_COM_MAP](#end_com_map)マクロを使用してマップを完了します。

### <a name="example"></a>例

ATL [BEEPER](../../overview/visual-cpp-samples.md)サンプルから:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>END_COM_MAP

COM インターフェイスマップの定義を終了します。

```
END_COM_MAP()
```

## <a name="see-also"></a>参照

[マクロ](../../atl/reference/atl-macros.md)<br/>
[COM マップに関するグローバル関数](../../atl/reference/com-map-global-functions.md)
