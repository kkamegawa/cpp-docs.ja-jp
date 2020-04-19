---
title: CManualAccessor クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 526415f14172911b26462fab97d9e0a7513b8cad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231065"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor クラス

高度な使用するために設計されたアクセサーの型を表します。

## <a name="syntax"></a>構文

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AddBindEntry](#addbindentry)|出力列にバインド エントリを追加します。|
|[AddParameterEntry](#addparameterentry)|パラメーターのアクセサーにパラメーターの入力を追加します。|
|[CreateAccessor](#createaccessor)|列バインド構造体のメモリを割り当て、列のデータ メンバーを初期化します。|
|[CreateParameterAccessor](#createparameteraccessor)|パラメーター バインド構造体のメモリを割り当て、パラメーターのデータ メンバーを初期化します。|

## <a name="remarks"></a>Remarks

使用して`CManualAccessor`実行時の関数呼び出しによって出力列のバインドと、パラメーターを指定できます。

## <a name="addbindentry"></a> CManualAccessor::AddBindEntry

出力列にバインド エントリを追加します。

### <a name="syntax"></a>構文

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列番号。

*wType*<br/>
[in]データを入力します。

*nColumnSize*<br/>
[in]列のサイズ (バイト単位)。

*pData*<br/>
[in]バッファーに格納されている列のデータへのポインター。

*pLength*<br/>
[in]必要な場合は、フィールドの長さへのポインター。

*pStatus*<br/>
[in]必要な場合は、列の状態にバインドする変数へのポインター。

### <a name="remarks"></a>Remarks

この関数を使用するには、まず[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)します。 指定された列の数よりも多くのエントリを追加することはできません`CreateAccessor`します。

## <a name="addparameterentry"></a> CManualAccessor::AddParameterEntry

パラメーターのエントリの構造体には、パラメーターの入力を追加します。

### <a name="syntax"></a>構文

```cpp
void AddParameterEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL,
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]パラメーターの数。

*wType*<br/>
[in]データを入力します。

*nColumnSize*<br/>
[in]列のサイズ (バイト単位)。

*pData*<br/>
[in]バッファーに格納されている列のデータへのポインター。

*pLength*<br/>
[in]必要な場合は、フィールドの長さへのポインター。

*pStatus*<br/>
[in]必要な場合は、列の状態にバインドする変数へのポインター。

*eParamIO*<br/>
[in]バインディングが関連付けられているパラメーターが、入力、入力/出力、または出力パラメーターであるかどうかを指定します。

### <a name="remarks"></a>Remarks

この関数を使用するには、まず[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)します。

## <a name="createaccessor"></a> Cmanualaccessor::createaccessor

列バインド構造体のメモリを割り当て、列のデータ メンバーを初期化します。

### <a name="syntax"></a>構文

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>パラメーター

*nBindEntries*<br/>
[in]列の数。 この数はへの呼び出しの数に一致する必要があります、 [cmanualaccessor::addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md)関数。

*pBuffer*<br/>
[in]出力列が格納されているバッファーへのポインター。

*nBufferSize*<br/>
[in]バッファーのバイト単位のサイズ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

呼び出す前に、この関数を呼び出し、`CManualAccessor::AddBindEntry`関数。

## <a name="createparameteraccessor"></a> Cmanualaccessor::createparameteraccessor

パラメーター バインド構造体のメモリを割り当て、パラメーターのデータ メンバーを初期化します。

### <a name="syntax"></a>構文

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>パラメーター

*nBindEntries*<br/>
[in]列の数。

*pBuffer*<br/>
[in]入力列が格納されているバッファーへのポインター。

*nBufferSize*<br/>
[in]バッファーのバイト単位のサイズ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

この関数を呼び出す前に呼び出す必要があります[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)します。

## <a name="see-also"></a>関連項目

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor クラス](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor クラス](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor クラス](../../data/oledb/cdynamicparameteraccessor-class.md)