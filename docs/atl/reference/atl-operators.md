---
title: ATL 演算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 6f1bd4f88b8d3a37f051a208a887c5264f61955a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260910"
---
# <a name="atl-operators"></a>ATL 演算子

このセクションには、ATL グローバル演算子のリファレンス トピックが含まれています。

|演算子|説明|
|--------------|-----------------|
|[operator ==](#operator_eq_eq)|2 つ`CSid`オブジェクトまたは`SID`構造体が等しいかどうか。|
|[operator !=](#operator_neq)|2 つ`CSid`オブジェクトまたは`SID`構造体が等しくないです。|
|[演算子 <](#operator_lt)|かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造体がより小さい`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。|
|[operator >](#operator_gt)|かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造体がより大きい、`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。|
|[operator <=](#operator_lt__eq)|かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造体は、以下に、`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。|
|[operator >=](#operator_gt__eq)|かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造がより大きいか等しい、`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity.h します。

##  <a name="operator_eq_eq"></a>  operator ==

比較`CSid`オブジェクトまたは`SID`(セキュリティ識別子) 構造体が等しいかどうか。

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
最初の`CSid`オブジェクトまたは`SID`比較する構造体。

*rhs*<br/>
2 番目の`CSid`オブジェクトまたは`SID`比較する構造体。

### <a name="return-value"></a>戻り値

かどうか、オブジェクトが等しいか、FALSE 等しくない場合は TRUE を返します。

##  <a name="operator_neq"></a>  演算子! =

比較`CSid`オブジェクトまたは`SID`(セキュリティ識別子) 構造体が等しくないです。

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
最初の`CSid`オブジェクトまたは`SID`比較する構造体。

*rhs*<br/>
2 番目の`CSid`オブジェクトまたは`SID`比較する構造体。

### <a name="return-value"></a>戻り値

オブジェクトが等しくない、等しい場合は FALSE がないかどうかは TRUE を返します。

##  <a name="operator_lt"></a>  演算子 <

かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造体がより小さい`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
最初の`CSid`オブジェクトまたは`SID`比較する構造体。

*rhs*<br/>
2 番目の`CSid`オブジェクトまたは`SID`比較する構造体。

### <a name="return-value"></a>戻り値

True の場合のアドレス、 *lhs*オブジェクトがのアドレスより小さい、 *rhs*オブジェクト、FALSE それ以外の場合。

### <a name="remarks"></a>Remarks

この演算子のアドレスに、`CSid`オブジェクトまたは`SID`構造体、および C++ 標準ライブラリ コレクション クラスとの互換性を提供する実装されます。

##  <a name="operator_gt"></a>  operator >

かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造体がより大きい、`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
最初の`CSid`オブジェクトまたは`SID`比較する構造体。

*rhs*<br/>
2 番目の`CSid`オブジェクトまたは`SID`比較する構造体。

### <a name="return-value"></a>戻り値

True の場合のアドレス、 *lhs*のアドレスより大きい、 *rhs*FALSE、それ以外の場合。

### <a name="remarks"></a>Remarks

この演算子のアドレスに、`CSid`オブジェクトまたは`SID`構造体、および C++ 標準ライブラリ コレクション クラスとの互換性を提供する実装されます。

##  <a name="operator_lt__eq"></a>  operator <=

かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造体は、以下に、`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
最初の`CSid`オブジェクトまたは`SID`比較する構造体。

*rhs*<br/>
2 番目の`CSid`オブジェクトまたは`SID`比較する構造体。

### <a name="return-value"></a>戻り値

True の場合のアドレス、 *lhs*が未満のアドレス、 *rhs*FALSE、それ以外の場合。

### <a name="remarks"></a>Remarks

この演算子のアドレスに、`CSid`オブジェクトまたは`SID`構造体、および C++ 標準ライブラリ コレクション クラスとの互換性を提供する実装されます。

##  <a name="operator_gt__eq"></a>  operator >=

かどうか、`CSid`オブジェクトまたは`SID`演算子の左側にある構造がより大きいか等しい、`CSid`オブジェクトまたは`SID`(C++ 標準ライブラリの互換性) の右側にある構造体。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
最初の`CSid`オブジェクトまたは`SID`比較する構造体。

*rhs*<br/>
2 番目の`CSid`オブジェクトまたは`SID`比較する構造体。

### <a name="return-value"></a>戻り値

場合に TRUE を返しますのアドレス、 *lhs*のアドレス以上、 *rhs*FALSE、それ以外の場合。

### <a name="remarks"></a>Remarks

この演算子のアドレスに、`CSid`オブジェクトまたは`SID`構造体、および C++ 標準ライブラリ コレクション クラスとの互換性を提供する実装されます。
