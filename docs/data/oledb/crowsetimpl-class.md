---
title: CRowsetImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 1fac3a74ca259fe3b680355fadc7f9bbd6e3cc13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368709"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl クラス

多くの実装インターフェイスの多重継承を必要とせず、標準の OLE DB 行セットの実装を提供します。

## <a name="syntax"></a>構文

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl : 
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ユーザーのクラスから派生した`CRowsetImpl`します。

*ストレージ*<br/>
ユーザー レコード クラスです。

*CreatorClass*<br/>
行セットのプロパティを含むクラス通常はコマンド。

*ArrayType*<br/>
行セットのデータ記憶域として機能するクラスです。 このパラメーターの既定値`CAtlArray`が必要な機能をサポートする任意のクラスができます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[NameFromDBID](#namefromdbid)|文字列を抽出、`DBID`にコピーし、 *bstr*で渡されます。|
|[SetCommandText](#setcommandtext)|検証し、格納、`DBID`で 2 つの文字列 ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md))。|

### <a name="overridable-methods"></a>オーバーライド可能なメソッド

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|特定のクライアント要求の列情報を取得します。|
|[GetCommandFromID](#getcommandfromid)|いずれかまたは両方のパラメーターには、文字列値が含まれている場合とそうである場合に表示するためのチェックは、データ メンバーに、文字列値をコピー [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md)します。|
|[ValidateCommandID](#validatecommandid)|参照のいずれかまたは両方をチェックします`DBID`s は、文字列の値が含まれ、場合は、そのデータ メンバーにコピー [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md)します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_rgRowData](#rgrowdata)|既定で、`CAtlArray`へのユーザー レコードのテンプレート引数に templatizes を`CRowsetImpl`します。 変更することで、もう 1 つの配列型のクラスを使用できます、`ArrayType`へのテンプレート引数`CRowsetImpl`します。|
|[m_strCommandText](#strcommandtext)|行セットの最初のコマンドが含まれています。|
|[m_strIndexText](#strindextext)|行セットの最初のインデックスが含まれています。|

## <a name="remarks"></a>Remarks

`CRowsetImpl` 静的キャストの形式での上書きを提供します。 メソッドは、指定された行セットがコマンド テキストを検証する方法を制御します。 独自に作成することができます`CRowsetImpl`-複数継承の実装のインターフェイスを作成してクラスのスタイルを設定します。 唯一のメソッドの実装を提供する必要があります`Execute`します。 作成メソッドによって作成する行セットの種類の異なるシグネチャを予想する`Execute`します。 たとえば、使用する場合、 `CRowsetImpl`-、スキーマ行セットを実装するクラスを派生、`Execute`メソッドは、次のシグネチャになります。

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

作成する場合、 `CRowsetImpl`-コマンドまたはセッションの行セットを実装するクラスを派生、`Execute`メソッドは、次のシグネチャになります。

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

いずれかを実装するために、 `CRowsetImpl`-派生`Execute`メソッドを内部データ バッファーを設定する必要があります ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md))。

## <a name="namefromdbid"></a> CRowsetImpl::NameFromDBID

文字列を抽出、`DBID`にコピーし、 *bstr*で渡されます。

### <a name="syntax"></a>構文

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>パラメーター

*pDBID*<br/>
[in]ポインター、`DBID`元の文字列を抽出します。

*bstr*<br/>
[in]A [CComBSTR](../../atl/reference/ccombstr-class.md)のコピーを配置への参照、`DBID`文字列。

*bIndex*<br/>
[in]**true**インデックス`DBID`;**false**テーブル`DBID`します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。 かどうかに応じて、`DBID`がテーブルまたはインデックス (によって示される*bIndex*)、DB_E_NOINDEX または DB_E_NOTABLE かメソッドを返します。

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、`CRowsetImpl`の実装[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)と[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)します。

## <a name="setcommandtext"></a> CRowsetImpl::SetCommandText

検証し、格納、`DBID`で 2 つの文字列 ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md))。

### <a name="syntax"></a>構文

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>パラメーター

*pTableID*<br/>
[in]ポインター、`DBID`テーブル ID を表す

*pIndexID*<br/>
[in]ポインター、`DBID`インデックス ID を表す

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

`SetCommentText`メソッドを呼び出して`CreateRowset`、静的なメソッドをテンプレート化`IOpenRowsetImpl`します。

このメソッドは、呼び出すことによって作業を委任[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)と[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)アップ キャストされたポインターを使用します。

## <a name="getcolumninfo"></a> CRowsetImpl::GetColumnInfo

特定のクライアント要求の列情報を取得します。

### <a name="syntax"></a>構文

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>パラメーター

*現在価値*<br/>
[in]ユーザーへのポインター`CRowsetImpl`クラスを派生します。

*pcCols*<br/>
[in]返される列の数には、(出力) のポインター。

### <a name="return-value"></a>戻り値

静的なへのポインター`ATLCOLUMNINFO`構造体。

### <a name="remarks"></a>Remarks

このメソッドは、高度なオーバーライドです。

このメソッドは、特定のクライアント要求の列情報を取得するいくつかの基本実装クラスによって呼び出されます。 通常は、このメソッドは、によって呼び出されると`IColumnsInfoImpl`します。 このメソッドをオーバーライドする場合は、メソッドは、のバージョンを配置する必要があります、 `CRowsetImpl`-クラスを派生します。 変更する必要があります、メソッドは、テンプレート化以外のクラスに配置することがあります、ため*pv*を適切な`CRowsetImpl`-クラスを派生します。

次の例で`GetColumnInfo`使用量。 この例で`CMyRowset`は、 `CRowsetImpl`-クラスを派生します。 オーバーライドするには`GetColumnInfo`をこのクラスのすべてのインスタンスの配置では、次のメソッド、`CMyRowset`クラスの定義。

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="getcommandfromid"></a> CRowsetImpl::GetCommandFromID

いずれかまたは両方のパラメーターには、文字列値が含まれている場合とそうである場合に表示するためのチェックは、データ メンバーに、文字列値をコピー [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md)します。

### <a name="syntax"></a>構文

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>パラメーター

*pTableID*<br/>
[in]ポインター、`DBID`表すテーブルの id。

*pIndexID*<br/>
[in]ポインター、`DBID`インデックスの ID を表す

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、静的キャスト`CRowsetImpl`データ メンバーを設定する[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md)します。 既定では、このメソッドは、いずれかまたは両方のパラメーターに文字列値が含まれているかどうかにチェックします。 文字列値が含まれている場合、このメソッドは、データ メンバーに文字列値をコピーします。 このシグネチャを持つメソッドを配置することで、 `CRowsetImpl`-派生クラスでは、基本の実装ではなく、メソッドが呼び出されます。

## <a name="validatecommandid"></a> CRowsetImpl::ValidateCommandID

参照のいずれかまたは両方をチェックします`DBID`s は、文字列の値が含まれ、場合は、そのデータ メンバーにコピー [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md)します。

### <a name="syntax"></a>構文

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>パラメーター

*pTableID*<br/>
[in]ポインター、`DBID`テーブル ID を表す

*pIndexID*<br/>
[in]ポインター、`DBID`インデックス ID を表す

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、静的キャスト`CRowsetImpl`そのデータ メンバーを設定する[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)と[その](../../data/oledb/crowsetimpl-m-strindextext.md)します。 既定では、このメソッドは参照のいずれかまたは両方をチェックします。 `DBID`s は、文字列の値が含まれると、場合は、そのデータ メンバーにコピーします。 このシグネチャを持つメソッドを配置することで、 `CRowsetImpl`-派生クラスでは、基本の実装ではなく、メソッドが呼び出されます。

## <a name="rgrowdata"></a> CRowsetImpl::m_rgRowData

既定で、`CAtlArray`へのユーザー レコードのテンプレート引数に templatizes を`CRowsetImpl`します。

### <a name="syntax"></a>構文

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Remarks

*ArrayType*をテンプレート パラメーターは、`CRowsetImpl`します。

## <a name="strcommandtext"></a> Crowsetimpl::m_strcommandtext

行セットの最初のコマンドが含まれています。

### <a name="syntax"></a>構文

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="strindextext"></a> CRowsetImpl::m_strIndexText

行セットの最初のインデックスが含まれています。

### <a name="syntax"></a>構文

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```