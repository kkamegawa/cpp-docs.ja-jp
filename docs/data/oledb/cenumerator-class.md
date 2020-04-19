---
title: CEnumerator クラス
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: 23467caf46d38175a74dab061f60e11009f1f481
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230841"
---
# <a name="cenumerator-class"></a>CEnumerator クラス

公開する OLE DB 列挙子オブジェクトを使用して、 [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85))インターフェイスをすべてのデータ ソースと列挙子を記述する行セットを返します。

## <a name="syntax"></a>構文

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[[検索]](#find)|指定した名前のいずれかを探して利用可能なプロバイダー (データ ソース) で検索します。|
|[GetMoniker](#getmoniker)|取得、`IMoniker`現在のレコードのインターフェイス。|
|[開く](#open)|列挙子を開きます。|

## <a name="remarks"></a>Remarks

取得することができます、`ISourcesRowset`このクラスから間接的にデータ。

## <a name="find"></a> Cenumerator::find

使用可能なプロバイダーの間で指定した名前を検索します。

### <a name="syntax"></a>構文

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>パラメーター

*szSearchName*<br/>
[in]検索する名前。

### <a name="return-value"></a>戻り値

**true**名前が見つかった場合します。 それ以外の場合、 **false**します。

### <a name="remarks"></a>Remarks

この名前にマップ、`SOURCES_NAME`のメンバー、 [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85))インターフェイス。

## <a name="getmoniker"></a> CEnumerator::GetMoniker

モニカーに変換できる文字列の部分を抽出する表示名を解析します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>パラメーター

*ppMoniker*<br/>
[out]表示名からモニカーが解析された ([cenumeratoraccessor::m_szparsename](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) 現在の行のできます。

*lpszDisplayName*<br/>
[in]解析する表示名。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="open"></a> Cenumerator::open

指定されている 1 つを呼び出して列挙子の行セットを取得します。 場合、列挙子のモニカーをバインド[isourcesrowset::getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85))します。

### <a name="syntax"></a>構文

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>パラメーター

*pMoniker*<br/>
[in]列挙子のモニカーへのポインター。

*pClsid*<br/>
[in]ポインター、`CLSID`の列挙子。

*enumerator*<br/>
[in]列挙子への参照。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="see-also"></a>関連項目

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)