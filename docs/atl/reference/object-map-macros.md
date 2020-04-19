---
title: オブジェクト マップに関するマクロ
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 73dc924527bac8499adefab3d0d6b51afa500a5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197381"
---
# <a name="object-map-macros"></a>オブジェクト マップに関するマクロ

これらのマクロは、オブジェクトのマップとエントリを定義します。

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|入力すると、オブジェクトのマップには、クラス オブジェクトのテキストの説明を指定することができます。|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|オブジェクト マップに ATL オブジェクトを入力、レジストリを更新し、オブジェクトのインスタンスを作成します。|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|オブジェクトを登録して初期化するように指定する一方で、`CoCreateInstance` を使用してオブジェクトを外部で作成できないように指定できます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION

クラスのオブジェクトのテキスト説明を指定することができます。

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>パラメーター

*x*<br/>
[in]クラス オブジェクトの説明です。

### <a name="remarks"></a>Remarks

ATL を介したオブジェクトのマップにこの説明を入力した、 [OBJECT_ENTRY_AUTO](#object_entry_auto)マクロ。

DECLARE_OBJECT_DESCRIPTION 実装、`GetObjectDescription`関数をオーバーライドする際、 [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription)メソッド。

`GetObjectDescription`関数`IComponentRegistrar::GetComponents`します。 `IComponentRegistrar` オートメーション インターフェイスを登録し、DLL 内の個々 のコンポーネントの登録を解除することができますです。 ATL プロジェクト ウィザードでコンポーネント レジストラー オブジェクトを作成するときに、ウィザードは自動的に実装、`IComponentRegistrar`インターフェイス。 `IComponentRegistrar` 通常、Microsoft Transaction Server によって使用されます。

ATL プロジェクト ウィザードの詳細については、記事を参照してください。 [ATL プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)です。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO

オブジェクト マップに ATL オブジェクトを入力、レジストリを更新し、オブジェクトのインスタンスを作成します。

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
[in]によって実装される COM クラスの CLSID、C++という名前のクラス*クラス*します。

*class*<br/>
[in]名前、C++によって表される COM クラスを実装するクラス*clsid*します。

### <a name="remarks"></a>Remarks

オブジェクトのエントリ マクロは、クラスの登録、初期化、および作成をサポートするためにプロジェクトのグローバル スコープに配置されます。

OBJECT_ENTRY_AUTO クリエーター クラスとクラス ファクトリ クリエーター クラスの関数ポインターを入力した`CreateInstance`ATL オブジェクトの自動生成されたマップには、このオブジェクトの関数。 ときに[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)が呼び出されると、オブジェクト マップ内の各オブジェクトのシステム レジストリを更新します。

次の表では、このマクロを 2 番目のパラメーターとして指定したクラスからオブジェクトのマップに追加される情報を取得する方法について説明します。

|情報|取得しました。|
|---------------------|-------------------|
|COM 登録|[レジストリに関するマクロ](../../atl/reference/registry-macros.md)|
|クラス ファクトリの作成|[クラス ファクトリに関するマクロ](../../atl/reference/aggregation-and-class-factory-macros.md)|
|インスタンスの作成|[集約マクロ](../../atl/reference/aggregation-and-class-factory-macros.md)|
|コンポーネント カテゴリの登録|[カテゴリに関するマクロ](../../atl/reference/category-macros.md)|
|クラス レベルの初期化とクリーンアップ|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

オブジェクトを登録して初期化するように指定する一方で、`CoCreateInstance` を使用してオブジェクトを外部で作成できないように指定できます。

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
[in]によって実装される COM クラスの CLSID、C++という名前のクラス*クラス*します。

*class*<br/>
[in]名前、C++によって表される COM クラスを実装するクラス*clsid*します。

### <a name="remarks"></a>Remarks

オブジェクトのエントリ マクロは、クラスの登録、初期化、および作成をサポートするためにプロジェクトのグローバル スコープに配置されます。

オブジェクトを登録して初期化することを指定する役立つことができます (を参照してください[OBJECT_ENTRY_AUTO](#object_entry_auto)詳細については) を使用して作成可能な型はありませんが、`CoCreateInstance`します。

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
