---
title: スナップイン オブジェクトに関するマクロ
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: b75dd04bed4895d722939d1bf9c0a6dfff2126e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276199"
---
# <a name="snap-in-object-macros"></a>スナップイン オブジェクトに関するマクロ

これらのマクロは、スナップインの拡張機能のサポートを提供します。

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|スナップイン オブジェクトのスナップイン拡張データ クラスのマップの先頭をマークします。|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|スナップイン オブジェクトのツールバーのマップの先頭をマークします。|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|スナップイン オブジェクトのスナップイン拡張データ クラスのマップの終了を示します。|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|スナップイン オブジェクトのマップをツールバーの最後をマークします。|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|スナップイン拡張機能のデータ クラスのデータ メンバーを作成します。|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|スナップイン オブジェクトのスナップイン拡張データ クラスのマップには、スナップインの拡張機能のデータ クラスを入力します。|
|[SNAPINMENUID](#snapinmenuid)|スナップイン オブジェクトによって使用されるコンテキスト メニューの ID を宣言します。|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|スナップイン オブジェクトのツールバーのマップをツールバーに入力します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsnap.h

##  <a name="begin_extension_snapin_nodeinfo_map"></a>  BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

スナップインの拡張機能のデータ クラスのマップの先頭をマークします。

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>パラメーター

*classname*<br/>
[in]スナップインの拡張機能のデータ クラスの名前。

### <a name="remarks"></a>Remarks

BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP マクロ拡張スナップインでマップを開始、スナップイン拡張データ型と型の各エントリを追加、 [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)マクロ、うえで、とマップ[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)マクロ。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="begin_snapintoolbarid_map"></a>  BEGIN_SNAPINTOOLBARID_MAP

スナップイン オブジェクトのツールバーの ID のマップの先頭を宣言します。

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>パラメーター

*_class*<br/>
[in]スナップイン オブジェクト クラスを指定します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

##  <a name="end_extension_snapin_nodeinfo_map"></a>  END_EXTENSION_SNAPIN_NODEINFO_MAP

スナップインの拡張機能のデータ クラスのマップの最後をマークします。

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Remarks

スナップイン拡張マップを開始、 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)マクロ、ごとに、拡張機能のスナップインからのデータ型のエントリを追加、 [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)マクロEND_EXTENSION_SNAPIN_NODEINFO_MAP マクロでマップを完了します。

### <a name="example"></a>例

例をご覧ください[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)します。

##  <a name="end_snapintoolbarid_map"></a>  END_SNAPINTOOLBARID_MAP

スナップイン オブジェクトのツールバーの ID のマップの末尾を宣言します。

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>パラメーター

*_class*<br/>
[in]スナップイン オブジェクト クラスを指定します。

### <a name="example"></a>例

例をご覧ください[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)します。

##  <a name="extension_snapin_dataclass"></a>  EXTENSION_SNAPIN_DATACLASS

スナップイン拡張データ クラスにデータ メンバーを追加、 **ISnapInItemImpl**-クラスを派生します。

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>パラメーター

*dataClass*<br/>
[in]スナップイン拡張機能のデータ クラス。

### <a name="remarks"></a>Remarks

このクラスは、スナップイン拡張データのクラスのマップにも入力する必要があります。 スナップイン拡張データ クラス マップを開始、 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)マクロ、スナップイン拡張データ型と型の各エントリを追加、 [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)マクロを含むマップを完了して、 [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)マクロ。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="extension_snapin_nodeinfo_entry"></a>  EXTENSION_SNAPIN_NODEINFO_ENTRY

スナップイン拡張データ クラスのマップには、スナップインの拡張機能のデータ クラスを追加します。

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>パラメーター

*dataClass*<br/>
[in]スナップイン拡張機能のデータ クラス。

### <a name="remarks"></a>Remarks

スナップイン拡張データ クラス マップを開始、 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)マクロ、EXTENSION_SNAPIN_NODEINFO_ENTRY のマクロを含む、スナップインの拡張機能のデータ型の各エントリを追加し、マップを完了[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)マクロ。

### <a name="example"></a>例

例をご覧ください[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)します。

##  <a name="snapinmenuid"></a>  SNAPINMENUID

このマクロを使用すると、スナップイン オブジェクトのコンテキスト メニュー リソースを宣言できます。

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
[in]スナップイン オブジェクトのコンテキスト メニューを識別します。

##  <a name="snapintoolbarid_entry"></a>  SNAPINTOOLBARID_ENTRY

このマクロを使用すると、スナップイン オブジェクトの ID のマップのツールバーに、ツールバーの ID を入力します。

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
[in]ツール バー コントロールを識別します。

### <a name="remarks"></a>Remarks

[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)マクロには、ツールバー ID のマップの先頭は[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)マクロは、終了をマークします。

### <a name="example"></a>例

例をご覧ください[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)します。

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
