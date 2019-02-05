---
title: CFileTimeSpan クラス
ms.date: 10/18/2018
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 8d384ced5de588a348eb72b9852697694b370ee4
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894160"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan クラス

このクラスは、相対的な日付と時刻の値がファイルへの関連付けを管理するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
class CFileTimeSpan
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|時間範囲を取得するには、このメソッドを呼び出す、`CFileTimeSpan`オブジェクト。|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|時間の範囲を設定するには、このメソッドを呼び出す、`CFileTimeSpan`オブジェクト。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|減算を実行する`CFileTimeSpan`オブジェクト。|
|[CFileTimeSpan::operator! =](#operator_neq)|2 つの `CFileTimeSpan` オブジェクトが等しくないかどうかを比較します。|
|[CFileTimeSpan::operator +](#operator_add)|加算を実行する、`CFileTimeSpan`オブジェクト。|
|[CFileTimeSpan::operator + =](#operator_add_eq)|加算を実行する、`CFileTimeSpan`オブジェクトし、結果を現在のオブジェクトに割り当てます。|
|[CFileTimeSpan::operator &lt;](#operator_lt)|2 つ`CFileTimeSpan`小さい方を決定するオブジェクト。|
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|2 つ`CFileTimeSpan`等値または小さい方を決定するオブジェクト。|
|[CFileTimeSpan::operator =](#operator_eq)|代入演算子です。|
|[CFileTimeSpan::operator -=](#operator_-_eq)|減算を実行、`CFileTimeSpan`オブジェクトし、結果を現在のオブジェクトに割り当てます。|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|2 つの `CFileTimeSpan` オブジェクトが等しいかどうかを比較します。|
|[CFileTimeSpan::operator &gt;](#operator_gt)|2 つ`CFileTimeSpan`うち、大きい方を決定するオブジェクト。|
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|2 つ`CFileTimeSpan`オブジェクトが等しいかどうか大きい方を判断します。|

## <a name="remarks"></a>Remarks

このクラスは、相対的な期間を管理するためのメソッドを提供します。 時刻の時に関する操作を実行するときに、発生頻度のファイルが作成、最後にアクセスまたは最後に変更します。 このクラスのメソッドが頻繁に使用と組み合わせて[CFileTime クラス](../../atl-mfc-shared/reference/cfiletime-class.md)オブジェクト。

## <a name="example"></a>例

例をご覧ください[CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atltime.h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

コンストラクターです。

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
既存の `CFileTimeSpan` オブジェクト。

*nSpan*<br/>
時間 (ミリ秒) の期間。

### <a name="remarks"></a>Remarks

`CFileTimeSpan`既存を使用してオブジェクトを作成できる`CFileTimeSpan`オブジェクト、または 64 ビット値として表されます。 既定のコンス トラクターは、時間間隔を 0 に設定します。

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

時間範囲を取得するには、このメソッドを呼び出す、`CFileTimeSpan`オブジェクト。

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>戻り値

時間間隔をミリ秒単位で返します。

##  <a name="operator_-"></a>  CFileTimeSpan::operator -

減算を実行する`CFileTimeSpan`オブジェクト。

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

返します、 `CFileTimeSpan` 2 つの時間範囲の差の結果を表すオブジェクト。

##  <a name="operator_neq"></a>  CFileTimeSpan::operator! =

2 つの `CFileTimeSpan` オブジェクトが等しくないかどうかを比較します。

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

比較対象となる項目が等しくない場合は TRUE を返します、`CFileTimeSpan`オブジェクト。 それ以外の場合に FALSE。

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

加算を実行する、`CFileTimeSpan`オブジェクト。

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

返します、`CFileTimeSpan`にまたがる 2 つの時間の合計を含むオブジェクトします。

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

加算を実行する、`CFileTimeSpan`オブジェクトし、現在のオブジェクトに、その結果を代入します。

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

更新された返します`CFileTimeSpan`にまたがる 2 つの時間の合計を含むオブジェクトします。

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

2 つ`CFileTimeSpan`小さい方を決定するオブジェクト。

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが小さい場合は TRUE を返します (つまりより短い期間を表します)、2 番目よりそれ以外の場合は FALSE。

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

2 つ`CFileTimeSpan`等値または小さい方を決定するオブジェクト。

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが (つまりより短い期間を表します) よりも小さい場合は TRUE。 または、2 番目を返します。 それ以外の場合は FALSE。

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

代入演算子です。

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

更新された返します`CFileTimeSpan`オブジェクト。

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator -=

減算を実行する`CFileTimeSpan`オブジェクトし、現在のオブジェクトに、その結果を代入します。

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

更新された返します`CFileTimeSpan`オブジェクト。

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

2 つの `CFileTimeSpan` オブジェクトが等しいかどうかを比較します。

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は、TRUE を返します。

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

2 つ`CFileTimeSpan`うち、大きい方を決定するオブジェクト。

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトがより大きい場合は TRUE を返します (つまりより長い期間を表します)、2 番目よりそれ以外の場合は FALSE。

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

2 つ`CFileTimeSpan`オブジェクトが等しいかどうか大きい方を判断します。

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトがより大きい場合は TRUE を返します (つまりより長い期間を表します)、2 番目に等しいまたはそれ以外の場合は FALSE。

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

時間の範囲を設定するには、このメソッドを呼び出す、`CFileTimeSpan`オブジェクト。

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>パラメーター

*nSpan*<br/>
ミリ秒単位で期間の新しい値。

## <a name="see-also"></a>関連項目

[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime クラス](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
