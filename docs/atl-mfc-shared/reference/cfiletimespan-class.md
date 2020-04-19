---
title: CFileTimeSpan クラス
description: Active Template Library (ATL) および Microsoft Foundation Classes (MFC) の CFileTimeSpan クラスは、FILETIME 単位の時間間隔を管理します。
ms.date: 01/10/2020
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
ms.openlocfilehash: 89d95759b11ff7e52c2a8fa75cf94f7b7b81fa36
ms.sourcegitcommit: c3283062ce4e382aec7f11626d358a37caf8cdbb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2020
ms.locfileid: "75914380"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan クラス

このクラスは、ファイルに関連付けられている相対的な日付と時刻の値を管理するためのメソッドを提供します。

## <a name="syntax"></a>構文

```cpp
class CFileTimeSpan
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|[名前]|説明|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|`CFileTimeSpan` オブジェクトから期間を取得するには、このメソッドを呼び出します。|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|`CFileTimeSpan` オブジェクトの期間を設定するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|[名前]|説明|
|----------|-----------------|
|[CFileTimeSpan:: operator-](#operator_-)|`CFileTimeSpan` オブジェクトに対して減算を実行します。|
|[CFileTimeSpan:: operator! =](#operator_neq)|2 つの `CFileTimeSpan` オブジェクトが等しくないかどうかを比較します。|
|[CFileTimeSpan:: operator +](#operator_add)|`CFileTimeSpan` オブジェクトに対して加算を実行します。|
|[CFileTimeSpan:: operator + =](#operator_add_eq)|`CFileTimeSpan` オブジェクトに対して加算を実行し、その結果を現在のオブジェクトに代入します。|
|[CFileTimeSpan:: operator &lt;](#operator_lt)|2つの `CFileTimeSpan` オブジェクトを比較して、小さい方を決定します。|
|[CFileTimeSpan:: operator &lt;=](#operator_lt_eq)|2つの `CFileTimeSpan` オブジェクトを比較して等価性または小さい方を判断します。|
|[CFileTimeSpan:: operator =](#operator_eq)|代入演算子。|
|[CFileTimeSpan:: operator-=](#operator_-_eq)|`CFileTimeSpan` オブジェクトに対して減算を実行し、その結果を現在のオブジェクトに代入します。|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|2 つの `CFileTimeSpan` オブジェクトが等しいかどうかを比較します。|
|[CFileTimeSpan:: operator &gt;](#operator_gt)|2つの `CFileTimeSpan` オブジェクトを比較して、大きい方を判断します。|
|[CFileTimeSpan:: operator &gt;=](#operator_gt_eq)|2つの `CFileTimeSpan` オブジェクトを比較して、等しいか、大きいかを判断します。|

## <a name="remarks"></a>Remarks

`CFileTimeSpan` クラスは、ファイルシステムが使用する単位の相対的な期間を処理するメソッドを提供します。 これらの単位は、ファイルが作成されたとき、最後にアクセスしたとき、または最後に変更されたときなど、ファイル操作でよく使用されます。 このクラスのメソッドは、 [CFileTime クラス](../../atl-mfc-shared/reference/cfiletime-class.md)オブジェクトと組み合わせて使用されることがよくあります。

## <a name="example"></a>使用例

[CFileTime:: ミリ秒](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)の例を参照してください。

## <a name="requirements"></a>要件

**ヘッダー:** atltime. h

## <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

コンストラクターです。

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
既存の `CFileTimeSpan` オブジェクト。

*Nspan*\
FILETIME 単位の期間。

### <a name="remarks"></a>Remarks

`CFileTimeSpan` オブジェクトは、既存の `CFileTimeSpan` オブジェクトを使用して作成することも、100ナノ秒の FILETIME 単位で64ビット値として表すこともできます。 詳細については、「 [CFileTime](cfiletime-class.md)」を参照してください。 既定のコンストラクターは、時間間隔を0に設定します。

## <a name="gettimespan"></a>CFileTimeSpan:: GetTimeSpan

`CFileTimeSpan` オブジェクトから期間を取得するには、このメソッドを呼び出します。

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>戻り値

100-ナノ秒の FILETIME 単位の時間間隔を返します。 詳細については、「 [CFileTime](cfiletime-class.md)」を参照してください。

## <a name="operator_-"></a>  CFileTimeSpan::operator -

`CFileTimeSpan` オブジェクトに対して減算を実行します。

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
`CFileTimeSpan` オブジェクトです。

### <a name="return-value"></a>戻り値

2つの期間の差の結果を表す `CFileTimeSpan` オブジェクトを返します。

## <a name="operator_neq"></a>CFileTimeSpan:: operator! =

2 つの `CFileTimeSpan` オブジェクトが等しくないかどうかを比較します。

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

比較対象の項目が `CFileTimeSpan` オブジェクトと等しくない場合は TRUE を返します。それ以外の場合は FALSE。

## <a name="operator_add"></a>CFileTimeSpan:: operator +

`CFileTimeSpan` オブジェクトに対して加算を実行します。

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
`CFileTimeSpan` オブジェクトです。

### <a name="return-value"></a>戻り値

2つの時間範囲の合計を格納している `CFileTimeSpan` オブジェクトを返します。

## <a name="operator_add_eq"></a>CFileTimeSpan:: operator + =

`CFileTimeSpan` オブジェクトに対する加算を実行し、その結果を現在のオブジェクトに代入します。

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
`CFileTimeSpan` オブジェクトです。

### <a name="return-value"></a>戻り値

2つの時間範囲の合計を格納している、更新された `CFileTimeSpan` オブジェクトを返します。

## <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

2つの `CFileTimeSpan` オブジェクトを比較して、小さい方を決定します。

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが2番目のオブジェクトよりも小さい (つまり、短い期間を表す) 場合は TRUE、それ以外の場合は FALSE を返します。

## <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

2つの `CFileTimeSpan` オブジェクトを比較して等価性または小さい方を判断します。

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトがより小さい場合 (つまり、より短い期間を表す)、または2番目のオブジェクトと等しい場合は TRUE、それ以外の場合は FALSE を返します。

## <a name="operator_eq"></a>CFileTimeSpan:: operator =

代入演算子。

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
`CFileTimeSpan` オブジェクトです。

### <a name="return-value"></a>戻り値

更新された `CFileTimeSpan` オブジェクトを返します。

## <a name="operator_-_eq"></a>CFileTimeSpan:: operator-=

`CFileTimeSpan` オブジェクトに対して減算を実行し、その結果を現在のオブジェクトに代入します。

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
`CFileTimeSpan` オブジェクトです。

### <a name="return-value"></a>戻り値

更新された `CFileTimeSpan` オブジェクトを返します。

## <a name="operator_eq_eq"></a>CFileTimeSpan:: operator = =

2 つの `CFileTimeSpan` オブジェクトが等しいかどうかを比較します。

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は TRUE、それ以外の場合は FALSE を返します。

## <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

2つの `CFileTimeSpan` オブジェクトを比較して、大きい方を判断します。

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが2番目のオブジェクトよりも大きい (つまり、より長い期間を表す) 場合は TRUE、それ以外の場合は FALSE を返します。

## <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

2つの `CFileTimeSpan` オブジェクトを比較して、等しいか、大きいかを判断します。

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*\
比較される `CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトがより大きい場合 (つまり、より長い期間を表す)、または2番目のオブジェクトと等しい場合は TRUE、それ以外の場合は FALSE を返します。

## <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

`CFileTimeSpan` オブジェクトの期間を設定するには、このメソッドを呼び出します。

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>パラメーター

*Nspan*\
100-ナノ秒の FILETIME 単位の期間の新しい値。 詳細については、「 [CFileTime](cfiletime-class.md)」を参照してください。

## <a name="see-also"></a>関連項目

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[CFileTime クラス](cfiletime-class.md)\
[階層図](../../mfc/hierarchy-chart.md)\
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
