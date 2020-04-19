---
title: CCustomSource (CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 296e7848b1d756fe0aba6156be2501db45bb092b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230557"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS.h)

プロバイダー クラスは、多重継承を使用します。 次のコードは、データ ソース オブジェクトの継承チェーンを示しています。

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

すべての COM コンポーネントが派生`CComObjectRootEx`と`CComCoClass`します。 `CComObjectRootEx` すべての実装を提供、`IUnknown`インターフェイス。 すべてのスレッド モデルを処理できます。 `CComCoClass` 必要なすべてのエラー サポートを処理します。 詳細なエラー情報をクライアントに送信する場合は、Api エラーの一部を使用で`CComCoClass`します。

データ ソース オブジェクトは、'Impl' のいくつかのクラスからも継承します。 各クラスは、インターフェイスの実装を提供します。 データ ソース オブジェクトの実装、 `IPersist`、 `IDBProperties`、 `IDBInitialize`、および`IDBCreateSession`インターフェイス。 各インターフェイスは、OLE DB データ ソース オブジェクトを実装するために必要です。 サポートするか、継承、またはこれら 'Impl' のクラスのいずれかから継承せずによって特定の機能をサポートしていませんを選択することができます。 サポートする場合、`IDBDataSourceAdmin`から継承するインターフェイス、`IDBDataSourceAdminImpl`クラスに必要な機能を取得します。

## <a name="com-map"></a>COM マップ

クライアントが呼び出すたびに`QueryInterface`インターフェイスについては、データ ソースで、次の COM マップ経由になります。

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource : 
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

すべての COM コンポーネントが派生`CComObjectRootEx`と`CComCoClass`します。 `CComObjectRootEx` すべての実装を提供、`IUnknown`インターフェイス。 すべてのスレッド モデルを処理できます。 `CComCoClass` 必要なすべてのエラー サポートを処理します。 詳細なエラー情報をクライアントに送信する場合は、Api エラーの一部を使用で`CComCoClass`します。

データ ソース オブジェクトは、'Impl' のいくつかのクラスからも継承します。 各クラスは、インターフェイスの実装を提供します。 データ ソース オブジェクトの実装、 `IPersist`、 `IDBProperties`、 `IDBInitialize`、および`IDBCreateSession`インターフェイス。 各インターフェイスは、OLE DB データ ソース オブジェクトを実装するために必要です。 サポートするか、継承、またはこれら 'Impl' のクラスのいずれかから継承せずによって特定の機能をサポートしていませんを選択することができます。 サポートする場合、`IDBDataSourceAdmin`から継承するインターフェイス、`IDBDataSourceAdminImpl`クラスに必要な機能を取得します。

## <a name="com-map"></a>COM マップ

クライアントが呼び出すたびに`QueryInterface`インターフェイスについては、データ ソースで、次の COM マップ経由になります。

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

COM_INTERFACE_ENTRY マクロが ATL からの通知の実装、`QueryInterface`で`CComObjectRootEx`を適切なインターフェイスを返します。

## <a name="property-map"></a>プロパティ マップ

プロパティ マップは、プロバイダーによって割り当てられたすべてのプロパティを指定します。

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)
      PROPERTY_INFO_ENTRY(CATALOGTERM)
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)
      PROPERTY_INFO_ENTRY(DATASOURCENAME)
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)
      PROPERTY_INFO_ENTRY(DBMSNAME)
      PROPERTY_INFO_ENTRY(DBMSVER)
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)
      PROPERTY_INFO_ENTRY(GROUPBY)
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)
      PROPERTY_INFO_ENTRY(NULLCOLLATION)
      PROPERTY_INFO_ENTRY(OLEOBJECTS)
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)
      PROPERTY_INFO_ENTRY(PROCEDURETERM)
      PROPERTY_INFO_ENTRY(PROVIDERNAME)
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)
      PROPERTY_INFO_ENTRY(PROVIDERVER)
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)
      PROPERTY_INFO_ENTRY(SCHEMATERM)
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)
      PROPERTY_INFO_ENTRY(SUBQUERIES)
      PROPERTY_INFO_ENTRY(TABLETERM)
      PROPERTY_INFO_ENTRY(USERNAME)
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)
      PROPERTY_INFO_ENTRY(AUTH_USERID)
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)
      PROPERTY_INFO_ENTRY(INIT_HWND)
      PROPERTY_INFO_ENTRY(INIT_LCID)
      PROPERTY_INFO_ENTRY(INIT_LOCATION)
      PROPERTY_INFO_ENTRY(INIT_MODE)
      PROPERTY_INFO_ENTRY(INIT_PROMPT)
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)
   END_PROPERTY_SET(DBPROPSET_DBINIT)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

OLE db プロパティのグループ化されます。 データ ソース オブジェクトが 2 つのグループのプロパティ: 設定、DBPROPSET_DATASOURCEINFO の 1 つと、DBPROPSET_DBINIT 設定に 1 つ。 DBPROPSET_DATASOURCEINFO セットは、プロバイダーとそのデータ ソースのプロパティに対応します。 DBPROPSET_DBINIT セットは、初期化時に使用されるプロパティに対応します。 OLE DB プロバイダー テンプレートは、PROPERTY_SET マクロでこれらのセットを処理します。 マクロは、プロパティの配列を含むブロックを作成します。 クライアントが呼び出すたびに、`IDBProperties`インターフェイス、プロバイダーは、プロパティ マップを使用します。

仕様のすべてのプロパティを実装する必要はありません。 ただし、必須のプロパティをサポートする必要があります。詳細については、レベル 0 への準拠の仕様を参照してください。 プロパティをサポートしない場合は、マップから削除できます。 プロパティをサポートする場合は、PROPERTY_INFO_ENTRY マクロを使用して、マップに追加、します。 マクロに対応する、`UPROPINFO`次のコードに示すように構造体します。

```cpp
struct UPROPINFO
{
   DBPROPID    dwPropId;
   ULONG       ulIDS;
   VARTYPE     VarType;
   DBPROPFLAGS dwFlags;
   union
   {
      DWORD dwVal;
      LPOLESTR szVal;
   };
   DBPROPOPTIONS dwOption;
};
```

構造内の各要素は、プロパティを処理するために情報を表します。 含まれている、`DBPROPID`プロパティの GUID と ID を確認します。 型とプロパティの値を特定のエントリも含まれています。

プロパティ (コンシューマーが、書き込み可能なプロパティの値をいつでもでも変更できることに注意してください) の既定値を変更する場合は、PROPERTY_INFO_ENTRY_VALUE または PROPERTY_INFO_ENTRY_EX マクロを使用できます。 これらのマクロを使用すると、対応するプロパティの値を指定できます。 PROPERTY_INFO_ENTRY_VALUE マクロとは、値を変更することを許可する簡便な表記法です。 PROPERTY_INFO_ENTRY_VALUE マクロは PROPERTY_INFO_ENTRY_EX マクロを呼び出します。 このマクロでは、すべての属性の変更を追加することができます、`UPROPINFO`構造体。

独自のプロパティ セットを定義する場合は、追加の BEGIN_PROPSET_MAP/END_PROPSET_MAP 組み合わせを 1 つを追加できます。 プロパティ セットの GUID を定義し、独自のプロパティを定義します。 プロバイダー固有のプロパティがある場合は、設定、既存のものを使用する代わりに新しいプロパティに追加します。 以降のバージョンの OLE DB での問題を回避できます。

## <a name="user-defined-property-sets"></a>ユーザー定義のプロパティ セット

Visual C では、ユーザー定義のプロパティ セットをサポートします。 オーバーライドする必要はありません`GetProperties`または`GetPropertyInfo`します。 代わりに、テンプレートでは、任意のユーザー定義のプロパティ セットを検出し、適切なオブジェクトに追加します。

初期化時に使用する必要があるユーザー定義のプロパティ セットがある場合 (つまり、コンシューマーを呼び出す前に`IDBInitialize::Initialize`)、BEGIN_PROPERTY_SET_EX マクロと共に UPROPSET_USERINIT フラグを使用してこれを指定することができます。 プロパティ セットは、これを行う (OLE DB 仕様が必要です)、データ ソース オブジェクトでなければなりません。 例:

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>関連項目

[プロバイダー ウィザードで生成されたファイル](../../data/oledb/provider-wizard-generated-files.md)<br/>
