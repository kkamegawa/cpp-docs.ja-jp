---
title: CComSafeArrayBound クラス
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: 0386092ac26e71fcf5e840594a6b07f56cc9badd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739749"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound クラス

このクラスは、 [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound)構造体のラッパーです。

## <a name="syntax"></a>構文

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|コンストラクターです。|
|[GetCount](#getcount)|要素の数を取得するには、このメソッドを呼び出します。|
|[GetLowerBound](#getlowerbound)|下限を返すには、このメソッドを呼び出します。|
|[System.array.getupperbound](#getupperbound)|上限を返すには、このメソッドを呼び出します。|
|[SetCount](#setcount)|要素の数を設定するには、このメソッドを呼び出します。|
|[SetLowerBound](#setlowerbound)|下限を設定するには、このメソッドを呼び出します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#operator_eq)|を新しい値に設定します。 `CComSafeArrayBound`|

## <a name="remarks"></a>Remarks

このクラスは、 [CComSafeArray](../../atl/reference/ccomsafearray-class.md)によっ`SAFEARRAYBOUND`て使用される構造体のラッパーです。 `CComSafeArray`オブジェクトの1つの次元の上限と下限、およびオブジェクトに含まれる要素の数を照会および設定するためのメソッドが用意されています。 多次元`CComSafeArray`オブジェクトは、各次元に`CComSafeArrayBound` 1 つずつ、オブジェクトの配列を使用します。 したがって、 [GetCount](#getcount)などのメソッドを使用する場合、このメソッドは多次元配列内の要素の合計数を返さないことに注意してください。

**ヘッダー:** atlsafe.h

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsafe.h

##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

コンストラクターです。

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>パラメーター

*ulCount*<br/>
配列の要素数。

*左辺のバインド*<br/>
配列の番号付け元となる下限。

### <a name="remarks"></a>Remarks

C++プログラムから配列にアクセスする場合は、下限を0として定義することをお勧めします。 配列を他の言語 (Visual Basic など) と共に使用する場合は、別の下限値を使用することをお勧めします。

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

要素の数を取得するには、このメソッドを呼び出します。

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>戻り値

要素の数を返します。

### <a name="remarks"></a>Remarks

関連付けられ`CComSafeArray`たオブジェクトが多次元配列を表している場合、このメソッドは、右端の次元にある要素の合計数のみを返します。 要素の合計数を取得するには、 [CComSafeArray:: GetCount](../../atl/reference/ccomsafearray-class.md#getcount)を使用します。

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

下限を返すには、このメソッドを呼び出します。

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>戻り値

`CComSafeArrayBound`オブジェクトの下限を返します。

##  <a name="getupperbound"></a>CComSafeArrayBound:: System.array.getupperbound

上限を返すには、このメソッドを呼び出します。

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>戻り値

`CComSafeArrayBound`オブジェクトの上限を返します。

### <a name="remarks"></a>Remarks

上限は、要素の数と下限の値によって異なります。 たとえば、下限が0で要素の数が10の場合、上限は自動的に9に設定されます。

##  <a name="operator_eq"></a>CComSafeArrayBound:: operator =

を新しい値に設定します。 `CComSafeArrayBound`

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>パラメーター

*バインディング*<br/>
`CComSafeArrayBound` オブジェクト。

*ulCount*<br/>
要素の数。

### <a name="return-value"></a>戻り値

オブジェクトへの`CComSafeArrayBound`ポインターを返します。

### <a name="remarks"></a>Remarks

オブジェクト`CComSafeArrayBound`は、既存`CComSafeArrayBound`のを使用するか、要素の数を指定することによって割り当てることができます。この場合、下限は既定で0に設定されます。

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

要素の数を設定するには、このメソッドを呼び出します。

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>パラメーター

*ulCount*<br/>
要素の数。

### <a name="return-value"></a>戻り値

`CComSafeArrayBound`オブジェクト内の要素の数を返します。

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

下限を設定するには、このメソッドを呼び出します。

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>パラメーター

*左辺のバインド*<br/>
下限。

### <a name="return-value"></a>戻り値

`CComSafeArrayBound`オブジェクトの新しい下限を返します。

### <a name="remarks"></a>Remarks

ビジュアルC++プログラムから配列にアクセスする場合は、下限を0として定義することをお勧めします。 配列を他の言語 (Visual Basic など) と共に使用する場合は、別の下限値を使用することをお勧めします。

上限は、要素の数と下限の値によって異なります。 たとえば、下限が0で要素の数が10の場合、上限は自動的に9に設定されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
