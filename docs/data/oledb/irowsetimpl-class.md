---
title: IRowsetImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: 47b03a542933c6223e098bc9d8fa8d45bf5e047b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390751"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl クラス

`IRowset` インターフェイスの実装を提供します。

## <a name="syntax"></a>構文

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`IRowsetImpl`します。

*RowsetInterface*<br/>
派生したクラス`IRowsetImpl`します。

*RowClass*<br/>
ストレージ ユニット、`HROW`します。

*MapClass*<br/>
プロバイダーによって保持されているすべての行ハンドルのストレージ ユニット。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AddRefRows](#addrefrows)|既存の行ハンドルには、参照カウントを追加します。|
|[CreateRow](#createrow)|によって呼び出される[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)を割り当てる新しい`HROW`します。 ユーザーが直接呼び出されません。|
|[GetData](#getdata)|行の行セットのコピーからデータを取得します。|
|[GetDBStatus](#getdbstatus)|指定したフィールドの状態を返します。|
|[GetNextRows](#getnextrows)|前の位置を記憶、順番に行をフェッチします。|
|[IRowsetImpl](#irowsetimpl)|コンストラクターです。 ユーザーが直接呼び出されません。|
|[RefRows](#refrows)|によって呼び出される[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)と[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)します。 ユーザーが直接呼び出されません。|
|[ReleaseRows](#releaserows)|行を解放します。|
|[RestartPosition](#restartposition)|次のフェッチ位置を初期位置に再配置します。つまり、行セットが最初の位置が作成されます。|
|[SetDBStatus](#setdbstatus)|指定したフィールドの状態フラグを設定します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|プロバイダーが後方フェッチをサポートしているかどうかを示します。|
|[m_bCanScrollBack](#bcanscrollback)|プロバイダーで内を後方に向かって、カーソルのスクロールができるかどうかを示します。|
|[m_bReset](#breset)|プロバイダーがカーソルの位置をリセットするかどうかを示します。 これは後方スクロールまたは下位のフェッチ時に特別な意味[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)します。|
|[m_iRowset](#irowset)|カーソルを表す行セットのインデックスです。|
|[m_rgRowHandles](#rgrowhandles)|行ハンドルの一覧。|

## <a name="remarks"></a>Remarks

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))は行セットの基本インターフェイスです。

## <a name="addrefrows"></a> IRowsetImpl::AddRefRows

既存の行ハンドルには、参照カウントを追加します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="createrow"></a> IRowsetImpl::CreateRow

によって呼び出されるヘルパー メソッド[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)を割り当てる新しい`HROW`します。

### <a name="syntax"></a>構文

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>パラメーター

*lRowsOffset*<br/>
作成されている行のカーソルの位置。

*cRowsObtained*<br/>
参照は、作成される行の数を示すユーザーに戻されます。

*rgRows*<br/>
配列の`HROW`新しく作成された行のハンドルを呼び出し元に返されます。

### <a name="remarks"></a>Remarks

このメソッドの呼び出し、行が存在する場合、 [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)を返します。 それ以外の場合、RowClass テンプレート変数の新しいインスタンスを割り当てしする追加[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)します。

## <a name="getdata"></a> IRowsetImpl::GetData

行の行セットのコピーからデータを取得します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>パラメーター

参照してください[irowset::getdata](/previous-versions/windows/desktop/ms716988(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

いくつかのパラメーターに対応*OLE DB プログラマーズ リファレンス*で説明されている別の名前のパラメーター `IRowset::GetData`:

|OLE DB テンプレート パラメーター|*OLE DB プログラマーズ リファレンス*パラメーター|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>Remarks

また、OLE DB データ変換 DLL を使用してデータ変換を処理します。

## <a name="getdbstatus"></a> Irowsetimpl::getdbstatus

指定したフィールドの DBSTATUS 状態フラグを返します。

### <a name="syntax"></a>構文

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>パラメーター

*currentRow*<br/>
[in]現在の行。

*columnNames*<br/>
[in]状態を要求する対象の列です。

### <a name="return-value"></a>戻り値

[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))列のフラグ。

## <a name="getnextrows"></a> IRowsetImpl::GetNextRows

前の位置を記憶、順番に行をフェッチします。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>パラメーター

参照してください[irowset::getnextrows](/previous-versions/windows/desktop/ms709827(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="irowsetimpl"></a> IRowsetImpl::IRowsetImpl

コンストラクターです。

### <a name="syntax"></a>構文

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Remarks

通常、このメソッドを直接呼び出す必要はありません。

## <a name="refrows"></a> IRowsetImpl::RefRows

によって呼び出される[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)と[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)をインクリメントするか、既存の行ハンドルの参照カウントを解放します。

### <a name="syntax"></a>構文

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>パラメーター

参照してください[IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

## <a name="releaserows"></a> IRowsetImpl::ReleaseRows

行を解放します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[::releaserows](/previous-versions/windows/desktop/ms719771(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="restartposition"></a> IRowsetImpl::RestartPosition

次のフェッチ位置を初期位置に再配置します。つまり、行セットが最初の位置が作成されます。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>パラメーター

参照してください[irowset::restartposition](/previous-versions/windows/desktop/ms712877(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="remarks"></a>Remarks

行セットの位置はまで未定義`GetNextRow`が呼び出されます。 呼び出して行セット内内を後方に向かって移動できます`RestartPosition`をフェッチするか、逆方向にスクロールします。

## <a name="setdbstatus"></a> Irowsetimpl::setdbstatus

指定したフィールドの DBSTATUS 状態フラグを設定します。

### <a name="syntax"></a>構文

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>パラメーター

*statusFlags*<br/>
[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))列に設定するフラグ。

*currentRow*<br/>
現在の行。

*columnInfo*<br/>
状態が設定されている列。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

プロバイダーは DBSTATUS_S_ISNULL と DBSTATUS_S_DEFAULT に対する特別な処理を提供するには、この関数をオーバーライドします。

## <a name="bcanfetchback"></a> IRowsetImpl::m_bCanFetchBack

プロバイダーが後方フェッチをサポートしているかどうかを示します。

### <a name="syntax"></a>構文

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Remarks

リンク、`DBPROP_CANFETCHBACKWARDS`プロパティ、`DBPROPSET_ROWSET`グループ。 プロバイダーをサポートする必要があります`DBPROP_CANFETCHBACKWARDS`の`m_bCanFetchBackwards`する**true**します。

## <a name="bcanscrollback"></a> IRowsetImpl::m_bCanScrollBack

プロバイダーで内を後方に向かって、カーソルのスクロールができるかどうかを示します。

### <a name="syntax"></a>構文

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Remarks

リンク、`DBPROP_CANSCROLLBACKWARDS`プロパティ、`DBPROPSET_ROWSET`グループ。 プロバイダーをサポートする必要があります`DBPROP_CANSCROLLBACKWARDS`の`m_bCanFetchBackwards`する**true**します。

## <a name="breset"></a> IRowsetImpl::m_bReset

行セットのカーソル位置が定義されているかどうかを判断するために使用するビット フラグです。

### <a name="syntax"></a>構文

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Remarks

コンシューマーから呼び出す場合[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) 、負の値と`lOffset`または*cRows*と`m_bReset`が true の場合`GetNextRows`を行セットの末尾に移動します。 場合`m_bReset`が false の場合、コンシューマーが OLE DB 仕様に準拠、エラー コードを受信します。 `m_bReset`にフラグが設定を取得**true**行セットが最初に作成されたときと、コンシューマーを呼び出すと[irowsetimpl::restartposition](../../data/oledb/irowsetimpl-restartposition.md)します。 設定**false**を呼び出すと`GetNextRows`します。

## <a name="irowset"></a> IRowsetImpl::m_iRowset

カーソルを表す行セットのインデックスです。

### <a name="syntax"></a>構文

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="rgrowhandles"></a> Irowsetimpl::m_rgrowhandles

現在、プロバイダーへの応答に含まれる行のハンドルのマップ`GetNextRows`します。

### <a name="syntax"></a>構文

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Remarks

行ハンドルを呼び出すことによって削除`ReleaseRows`します。 参照してください、 [IRowsetImpl 概要](../../data/oledb/irowsetimpl-class.md)の定義の*MapClass*します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow クラス](../../data/oledb/csimplerow-class.md)