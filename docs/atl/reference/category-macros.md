---
title: カテゴリマクロ
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 411e06cc795827eef356018ba427510fd9eb7c06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497854"
---
# <a name="category-macros"></a>カテゴリマクロ

これらのマクロは、カテゴリマップを定義します。

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|カテゴリマップの先頭をマークします。|
|[END_CATEGORY_MAP](#end_category_map)|カテゴリマップの終了をマークします。|
|[IMPLEMENTED_CATEGORY](#implemented_category)|COM オブジェクトによって実装されるカテゴリを示します。|
|[REQUIRED_CATEGORY](#required_category)|COM オブジェクトによってコンテナーに必要なカテゴリを示します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

カテゴリマップの先頭をマークします。

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
からカテゴリマップを格納しているクラスの名前。

### <a name="remarks"></a>Remarks

Category マップは、COM クラスが実装するコンポーネントカテゴリと、そのコンテナーから必要なカテゴリを指定するために使用されます。

COM クラスによって実装されている各カテゴリのマップに[IMPLEMENTED_CATEGORY](#implemented_category)エントリを追加します。 クラスがクライアントを実装する必要がある各カテゴリのマップに[REQUIRED_CATEGORY](#required_category)エントリを追加します。 マップの末尾に[END_CATEGORY_MAP](#end_category_map)マクロを設定します。

クラスに[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)または[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)が関連付けられている場合、モジュールが登録されると、マップに表示されるコンポーネントカテゴリが自動的に登録されます。

> [!NOTE]
>  ATL では、標準のコンポーネントカテゴリマネージャーを使用して、コンポーネントカテゴリを登録します。 モジュールが登録されているときに、マネージャーがシステムに存在しない場合、登録は成功しますが、そのクラスにはコンポーネントカテゴリが登録されません。

コンポーネントカテゴリの詳細については、「[コンポーネントカテゴリとは」および](/windows/win32/com/component-categories-and-how-they-work)「Windows SDK での動作のしくみ」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>  END_CATEGORY_MAP

カテゴリマップの終了をマークします。

```
END_CATEGORY_MAP()
```

### <a name="example"></a>例

[BEGIN_CATEGORY_MAP](#begin_category_map)の例を参照してください。

##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY

コンポーネントの[カテゴリマップ](#begin_category_map)に IMPLEMENTED_CATEGORY マクロを追加して、 *catID*パラメーターで識別されるカテゴリの実装として登録する必要があることを指定します。

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>パラメーター

*catID*<br/>
から実装されているカテゴリのグローバル一意識別子 (GUID) を保持する CATID 定数または変数。 *CatID*のアドレスが取得され、マップに追加されます。 ストックカテゴリの選択については、次の表を参照してください。

### <a name="remarks"></a>Remarks

クラスに関連付けられた[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)または[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)マクロがある場合は、モジュールが登録されると、マップに表示されるコンポーネントカテゴリが自動的に登録されます。

クライアントは、クラスに登録されているカテゴリ情報を使用して、そのクラスのインスタンスを作成することなく、その機能と要件を決定できます。

コンポーネントカテゴリの詳細については、「[コンポーネントカテゴリとは」および](/windows/win32/com/component-categories-and-how-they-work)「Windows SDK での動作のしくみ」を参照してください。

### <a name="a-selection-of-stock-categories"></a>ストックカテゴリの選択

|説明|シンボル|レジストリ GUID|
|-----------------|------------|-------------------|
|スクリプトに対して安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|初期化に対して安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|単純なフレームサイトの含有|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|単純データ バインディング|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|高度なデータバインディング|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|ウィンドウなしのコントロール|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|インターネット対応オブジェクト|サンプル一覧については、「Windows SDK の[インターネット対応オブジェクト](/windows/win32/com/internet-aware-objects)」を参照してください。||

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>REQUIRED_CATEGORY

コンポーネントの[カテゴリマップ](#begin_category_map)に REQUIRED_CATEGORY マクロを追加して、 *catID*パラメーターで識別されるカテゴリを要求するように登録する必要があることを指定します。

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>パラメーター

*catID*<br/>
から必須カテゴリのグローバル一意識別子 (GUID) を保持する CATID 定数または変数。 *CatID*のアドレスが取得され、マップに追加されます。 ストックカテゴリの選択については、次の表を参照してください。

### <a name="remarks"></a>Remarks

クラスに関連付けられた[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)または[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)マクロがある場合は、モジュールが登録されると、マップに表示されるコンポーネントカテゴリが自動的に登録されます。

クライアントは、クラスに登録されているカテゴリ情報を使用して、そのクラスのインスタンスを作成することなく、その機能と要件を決定できます。 たとえば、コントロールでは、コンテナーがデータバインディングをサポートしている必要があります。 コンテナーは、そのコントロールが必要とするカテゴリのカテゴリマネージャーに対してクエリを実行することで、コントロールをホストするために必要な機能があるかどうかを確認できます。 コンテナーが必要な機能をサポートしていない場合、COM オブジェクトのホストを拒否することができます。

サンプルリストを含むコンポーネントカテゴリの詳細については、「[コンポーネントのカテゴリとは」および](/windows/win32/com/component-categories-and-how-they-work)「Windows SDK での動作のしくみ」を参照してください。

### <a name="a-selection-of-stock-categories"></a>ストックカテゴリの選択

|説明|シンボル|レジストリ GUID|
|-----------------|------------|-------------------|
|スクリプトに対して安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|初期化に対して安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|単純なフレームサイトの含有|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|単純データ バインディング|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|高度なデータバインディング|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|ウィンドウなしのコントロール|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|インターネット対応オブジェクト|サンプル一覧については、「Windows SDK の[インターネット対応オブジェクト](/windows/win32/com/internet-aware-objects)」を参照してください。||

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
