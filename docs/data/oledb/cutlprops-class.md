---
title: CUtlProps クラス
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- CUtlProps
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: 3f1af90bcf454a3651dd8de65bbee7cb6b5960ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176123"
---
# <a name="cutlprops-class"></a>CUtlProps クラス

OLE DB プロパティのインターフェイスのさまざまなプロパティを実装する (たとえば、 `IDBProperties`、 `IDBProperties`、および`IRowsetInfo`)。

## <a name="syntax"></a>構文

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>パラメーター

*T*<br/>
含むクラス、`BEGIN_PROPSET_MAP`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[GetPropValue](#getpropvalue)|プロパティのセットからプロパティを取得します。|
|[IsValidValue](#isvalidvalue)|プロパティを設定する前に、値を検証するために使用します。|
|[OnInterfaceRequested](#oninterfacerequested)|コンシューマーは、オブジェクト作成インターフェイスのメソッドを呼び出すときは、省略可能なインターフェイスの要求を処理します。|
|[OnPropertyChanged](#onpropertychanged)|チェーンされたプロパティを処理するためにプロパティを設定した後に呼び出されます。|
|[SetPropValue](#setpropvalue)|プロパティ セットのプロパティを設定します。|

## <a name="remarks"></a>Remarks

このクラスのほとんどは、実装の詳細です。

`CUtlProps` 内部的にプロパティを設定するため、2 つのメンバーが含まれています。[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)と[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)します。

プロパティ セットのマップで使用されるマクロの詳細については、次を参照してください。 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)と[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)します。

## <a name="getpropvalue"></a> CUtlProps::GetPropValue

プロパティのセットからプロパティを取得します。

### <a name="syntax"></a>構文

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>パラメーター

*pguidPropSet*<br/>
[in]PropSet の GUID です。

*dwPropId*<br/>
[in]プロパティのインデックス。

*pvValue*<br/>
[out]新しいプロパティ値を含んでいるバリアントへのポインター。

### <a name="return-value"></a>戻り値

`Failure` 障害と正常終了した場合。

## <a name="isvalidvalue"></a> CUtlProps::IsValidValue

プロパティを設定する前に、値を検証するために使用します。

### <a name="syntax"></a>構文

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>パラメーター

*iCurSet*<br/>
プロパティ セットの配列インデックス1 つのプロパティ セットがある場合は 0 します。

*pDBProp*<br/>
プロパティ ID と新しい値を[DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))構造体。

### <a name="return-value"></a>戻り値

標準の HRESULT です。 既定の戻り値は、S_OK です。

### <a name="remarks"></a>Remarks

を使用して、プロパティを設定しようとしている値で実行する検証ルーチンがある場合は、この関数をオーバーライドする必要があります。 たとえば、有効な値を決定するパスワード テーブルに対して DBPROP_AUTH_PASSWORD を検証する可能性があります。

## <a name="oninterfacerequested"></a> CUtlProps::OnInterfaceRequested

コンシューマーでメソッドを呼び出し、オブジェクトのいずれかのインターフェイスの作成時に、省略可能なインターフェイスの要求を処理します。

### <a name="syntax"></a>構文

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>パラメーター

*riid*<br/>
[in]要求されたインターフェイスの IID。 詳細については、の説明を参照して、 *riid*パラメーターの`ICommand::Execute`で、 *OLE DB プログラマーズ リファレンス*(で、 *MDAC SDK*)。

### <a name="remarks"></a>Remarks

`OnInterfaceRequested` コンシューマーでメソッドを呼び出し、オブジェクトのいずれかのインターフェイスの作成時に、省略可能なインターフェイスのコンシューマーの要求を処理 (など`IDBCreateSession`、 `IDBCreateCommand`、 `IOpenRowset`、または`ICommand`)。 要求されたインターフェイスに対応する OLE DB プロパティを設定します。 たとえば、コンシューマーが要求する`IID_IRowsetLocate`、`OnInterfaceRequested`設定、`DBPROP_IRowsetLocate`インターフェイス。 これにより行セットの作成時に適切な状態を維持します。

コンシューマーを呼び出すと、このメソッドが呼び出されます`IOpenRowset::OpenRowset`または`ICommand::Execute`します。

コンシューマーは、オブジェクトを開き、オプションのインターフェイスを要求する、プロバイダーを VARIANT_TRUE にそのインターフェイスに関連付けられたプロパティを設定する必要があります。 プロパティに固有の処理を許可する`OnInterfaceRequested`プロバイダーの前に呼び出されます`Execute`メソッドが呼び出されます。 既定では、`OnInterfaceRequested`次のインターフェイスを処理します。

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

その他のインターフェイスを処理する場合は、関数を処理するデータ ソース、セッション、コマンド、または行セット クラスでは、この関数をオーバーライドします。 オーバーライドは、プロパティを設定すると、連鎖プロパティも設定されることを確認する通常の設定/取得するプロパティのインターフェイスを通過する必要があります (を参照してください[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md))。

## <a name="onpropertychanged"></a> CUtlProps::OnPropertyChanged

チェーンされたプロパティを処理するためにプロパティを設定した後に呼び出されます。

### <a name="syntax"></a>構文

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>パラメーター

*iCurSet*<br/>
プロパティ セットの配列インデックス1 つのプロパティ セットがある場合は 0 します。

*pDBProp*<br/>
プロパティ ID と新しい値を[DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))構造体。

### <a name="return-value"></a>戻り値

標準の HRESULT です。 既定の戻り値は、S_OK です。

### <a name="remarks"></a>Remarks

チェーンされたプロパティ、ブックマーク、値がもう 1 つのプロパティの値に依存する更新プログラムなどを処理する場合は、この関数をオーバーライドする必要があります。

### <a name="example"></a>例

この関数で、ユーザー ID を取得しますプロパティから、`DBPROP*`パラメーター。 チェーンのプロパティに対して ID を比較することができます。 プロパティが見つかった場合`SetProperties`は他のプロパティと共に設定するプロパティを持つと呼びます。 この場合、いずれかを取得する場合、 `DBPROP_IRowsetLocate`、 `DBPROP_LITERALBOOKMARKS`、または`DBPROP_ORDEREDBOOKMARKS`プロパティ、いずれかの設定、`DBPROP_BOOKMARKS`プロパティ。

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="setpropvalue"></a> CUtlProps::SetPropValue

プロパティ セットのプロパティを設定します。

### <a name="syntax"></a>構文

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>パラメーター

*pguidPropSet*<br/>
[in]PropSet の GUID です。

*dwPropId*<br/>
[in]プロパティのインデックス。

*pvValue*<br/>
[in]新しいプロパティ値を含んでいるバリアントへのポインター。

### <a name="return-value"></a>戻り値

`Failure` 障害と正常終了した場合。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)