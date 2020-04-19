---
title: CTable クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: fab1ba2e496f4945eb56c0a67b833f6bf063404e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368436"
---
# <a name="ctable-class"></a>CTable クラス

(パラメーターなしのいずれかの) 単純な行セットに直接アクセスするための手段を提供します。

## <a name="syntax"></a>構文

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>パラメーター

*TAccessor*<br/>
アクセサー クラス。

*TRowset*<br/>
行セット クラスです。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[開く](#open)|テーブルを開きます。|

## <a name="remarks"></a>Remarks

参照してください[CCommand](../../data/oledb/ccommand-class.md)については、行セットにアクセスするためのコマンドを実行する方法。

## <a name="open"></a> Ctable::open

テーブルを開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   LPCSTR szTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   DBID& dbid,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();
```

#### <a name="parameters"></a>パラメーター

*session*<br/>
[in]テーブルが開いているセッションです。

*wszTableName*<br/>
[in]開くには、テーブルの名前は、Unicode 文字列として渡されます。

*szTableName*<br/>
[in]開くには、テーブルの名前は、ANSI 文字列として渡されます。

*dbid*<br/>
[in]`DBID`のテーブルを開きます。

*pPropSet*<br/>
[in]配列へのポインター [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))プロパティおよび設定する値を含む構造体。 参照してください[プロパティ セットとプロパティ グループ](/previous-versions/windows/desktop/ms713696(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*Windows SDK にします。 既定値は NULL には、プロパティは指定しません。

*ulPropSets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))構造体が渡された、 *pPropSet*引数。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [iopenrowset::openrowset](/previous-versions/windows/desktop/ms716724(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)