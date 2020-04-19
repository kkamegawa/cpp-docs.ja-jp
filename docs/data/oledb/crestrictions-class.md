---
title: CRestrictions クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 309bb7e707d649cf78528f3d0df6cf8e43201823
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361881"
---
# <a name="crestrictions-class"></a>CRestrictions クラス

ジェネリック クラスには、スキーマ行セットの制限を指定することができます。

## <a name="syntax"></a>構文

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
アクセサーに使用されるクラス。

*nRestrictions*<br/>
スキーマ行セットの制限列の数。

*pguid*<br/>
スキーマの GUID へのポインター。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbsch.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[開く](#open)|ユーザーが指定した制限に従って、結果セットを返します。|

## <a name="open"></a> Crestrictions::open

ユーザーが指定した制限に従って、結果セットを返します。

### <a name="syntax"></a>構文

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>パラメーター

*session*<br/>
[in]データ ソースに接続するため、既存のセッション オブジェクトを指定します。

*lpszParam*<br/>
[in]スキーマ行セットに対して制限を指定します。

*bBind*<br/>
[in]列マップを自動的にバインドするかどうかを指定します。 既定値は**true**、これにより、列マップが自動的に連結されます。 設定*bBind*に**false**手動でバインドできるように、列マップの自動に連結します。 (手動バインドは、OLAP ユーザーにとって特に重要ですが) です。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

スキーマ行セットでは、7 個の制限の最大数を指定できます。

参照してください[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))定義されている制限については、各スキーマ行セットにします。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[スキーマ行セット クラスと Typedef クラス](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)