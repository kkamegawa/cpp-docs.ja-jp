---
title: IRowsetChangeImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: 8b2a92fdefd965d4b87e0a9ed411cc1b5c89b8f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390764"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl クラス

OLE DB テンプレートの実装、 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) OLE DB 仕様のインターフェイス。

## <a name="syntax"></a>構文

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス`IRowsetChangeImpl`します。

*ストレージ*<br/>
ユーザー レコード。

*BaseInterface*<br/>
基底クラス、インターフェイスでなど`IRowsetChange`します。

*RowClass*<br/>
行ハンドルの記憶域ユニット。

*MapClass*<br/>
プロバイダーによって保持されているすべての行ハンドルのストレージ ユニット。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="interface-methods-used-with-irowsetchange"></a>インターフェイスのメソッド (IRowsetChange で使用)

|||
|-|-|
|[DeleteRows](#deleterows)|行セットから行を削除します。|
|[InsertRow](#insertrow)|行セットには、行を挿入します。|
|[SetData](#setdata)|1 つまたは複数の列のデータ値を設定します。|

### <a name="implementation-method-callback"></a>実装メソッド (コールバック)

|||
|-|-|
|[FlushData](#flushdata)|データをそのストアにコミットするためのプロバイダーでオーバーライドします。|

## <a name="remarks"></a>Remarks

このインターフェイスは、データ ストアへの即時の書き込み操作を担当します。 「直近」の意味がエンドユーザー (コンシューマーを使用するユーザー) がすべての変更を行うと、それらの変更はすぐに送信されること、データは格納 (および、元に戻すことはできません)。

`IRowsetChangeImpl` OLE DB 実装`IRowsetChange`インターフェイスで、行を削除して、新しい行を挿入する既存の行の列の値の更新が可能です。

OLE DB テンプレートの実装には、すべての基本メソッドがサポートしています (`SetData`、 `InsertRow`、および`DeleteRows`)。

> [!IMPORTANT]
>  プロバイダーを実装する前に、次のドキュメントを確認することを強くお勧めします。

- [更新可能なプロバイダーの作成](../../data/oledb/creating-an-updatable-provider.md)

- 第 6 章、 *OLE DB プログラマーズ リファレンス*

- 参照してください、`RUpdateRowset`クラスが使用されて、 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)サンプル。

## <a name="deleterows"></a> IRowsetChangeImpl::DeleteRows

行セットから行を削除します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[irowsetchange::deleterows](/previous-versions/windows/desktop/ms724362(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="insertrow"></a> IRowsetChangeImpl::InsertRow

作成し、行セット内の新しい行を初期化します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>パラメーター

参照してください[irowsetchange::insertrow](/previous-versions/windows/desktop/ms716921(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="setdata"></a> IRowsetChangeImpl::SetData

1 つまたは複数の列のデータ値を設定します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>パラメーター

参照してください[irowsetchange::setdata](/previous-versions/windows/desktop/ms721232(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="flushdata"></a> IRowsetChangeImpl::FlushData

データをそのストアにコミットするためのプロバイダーでオーバーライドします。

### <a name="syntax"></a>構文

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>パラメーター

*hRowToFlush*<br/>
[in]データの行へのハンドルします。 この行の型から判断されます、 *RowClass*のテンプレート引数、`IRowsetImpl`クラス (`CSimpleRow`既定)。

*hAccessorToFlush*<br/>
[in]バインド情報とで型情報が含まれた、アクセサーへのハンドル、 `PROVIDER_MAP` (を参照してください[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md))。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)