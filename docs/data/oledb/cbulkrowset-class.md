---
title: CBulkRowset クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: ba6b41a708cd854e398cbaa80609472ebbe167e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176470"
---
# <a name="cbulkrowset-class"></a>CBulkRowset クラス

フェッチして、単一の呼び出しで複数の行ハンドルを取得することによって、データの一括で動作する行を操作できます。

## <a name="syntax"></a>構文

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>パラメーター

*TAccessor*<br/>
アクセサー クラス。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AddRefRows](#addrefrows)|参照カウントをインクリメントします。|
|[CBulkRowset](#cbulkrowset)|コンストラクターです。|
|[MoveFirst](#movefirst)|必要に応じて新しい一括フェッチを実行して、データの最初の行を取得します。|
|[MoveLast](#movelast)|最後の行に移動します。|
|[MoveNext](#movenext)|次のデータ行を取得します。|
|[MovePrev](#moveprev)|前の行に移動します。|
|[MoveToBookmark](#movetobookmark)|ブックマークからブックマークで行または指定したオフセットの行をフェッチします。|
|[MoveToRatio](#movetoratio)|行セット内の小数部の位置から始まる行がフェッチされます。|
|[ReleaseRows](#releaserows)|現在の行を設定します (`m_nCurrentRow`) すべての行が 0 のリリース。|
|[SetRows](#setrows)|1 回の呼び出しによって取得する行ハンドルの数を設定します。|

## <a name="example"></a>例

次の例での使用、`CBulkRowset`クラス。

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="addrefrows"></a> CBulkRowset::AddRefRows

呼び出し[IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) bulk 行セットから取得した現在のすべての行の参照カウントをインクリメントします。

### <a name="syntax"></a>構文

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="cbulkrowset"></a> CBulkRowset::CBulkRowset

新たに作成`CBulkRowset`オブジェクトし、既定行の数を 10 に設定します。

### <a name="syntax"></a>構文

```cpp
CBulkRowset();
```

## <a name="movefirst"></a> CBulkRowset::MoveFirst

データの最初の行を取得します。

### <a name="syntax"></a>構文

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="movelast"></a> CBulkRowset::MoveLast

最後の行に移動します。

### <a name="syntax"></a>構文

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="movenext"></a> CBulkRowset::MoveNext

次のデータ行を取得します。

### <a name="syntax"></a>構文

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT です。 行セットの末尾に達している場合は、DB_S_ENDOFROWSET を返します。

## <a name="moveprev"></a> CBulkRowset::MovePrev

前の行に移動します。

### <a name="syntax"></a>構文

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="movetobookmark"></a> CBulkRowset::MoveToBookmark

ブックマークまたは、指定したオフセットの行でマークされた行をフェッチ (*した*)、そのブックマークから。

### <a name="syntax"></a>構文

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>パラメーター

*ブックマーク*<br/>
[in]データをフェッチする位置を示すブックマーク。

*した*<br/>
[in]対象の行にブックマークからの行の数。 場合*した*0 の場合は、フェッチされる最初の行は、ブックマークが設定された行。 場合*した*は 1 です。 最初の行がフェッチされた行の直後、行は、します。 場合*した*-1 で、フェッチされる最初の行は、ブックマークが設定された行の前に行。

### <a name="return-value"></a>戻り値

参照してください[irowset::getdata](/previous-versions/windows/desktop/ms716988(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="movetoratio"></a> CBulkRowset::MoveToRatio

行セット内の小数部の位置から始まる行がフェッチされます。

### <a name="syntax"></a>構文

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>パラメーター

*nNumerator*<br/>
[in]分子からデータをフェッチする小数部の位置を決定するために使用します。

*nDenominator*<br/>
[in]元のデータをフェッチする小数部の位置を決定するために使用する分母。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

`MoveToRatio` 次の数式に従ってほぼ行がフェッチされます。

`(nNumerator *  RowsetSize ) / nDenominator`

場所`RowsetSize`行数で指定された行セットのサイズです。 この式の精度は、特定のプロバイダーによって異なります。 詳細については、次を参照してください。 [irowsetscroll::getrowsatratio](/previous-versions/windows/desktop/ms709602(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="releaserows"></a> CBulkRowset::ReleaseRows

呼び出し[::releaserows](/previous-versions/windows/desktop/ms719771(v=vs.85)) bulk 行セットから取得した現在のすべての行の参照カウントをデクリメントします。

### <a name="syntax"></a>構文

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="setrows"></a> CBulkRowset::SetRows

各呼び出しによって取得する行ハンドルの数を設定します。

### <a name="syntax"></a>構文

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>パラメーター

*nRows*<br/>
[in]行セット (行の数) の新しいサイズ。

### <a name="remarks"></a>Remarks

この関数を呼び出す場合は、行セットが開かれる前にあります。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)