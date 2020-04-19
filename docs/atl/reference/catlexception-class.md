---
title: CAtlException クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: a6ed6062be02fddc111e4eda4d26226b7a7a0c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260676"
---
# <a name="catlexception-class"></a>CAtlException クラス

このクラスは、ATL の例外を定義します。

## <a name="syntax"></a>構文

```
class CAtlException
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|コンストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAtlException::operator HRESULT](#operator_hresult)|HRESULT 値を現在のオブジェクトにキャストします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|型の変数 HRESULT は、オブジェクトによって作成され、エラー状態を格納するために使用します。|

## <a name="remarks"></a>Remarks

A`CAtlException`オブジェクトは、ATL 操作に関する例外条件を表します。 `CAtlException`クラスにキャスト演算子を使用すると、HRESULT の場合と同様に、例外を処理して、例外の原因を示すステータス コードを格納するパブリック データ メンバーが含まれています。

一般を呼び出す`AtlThrow`を作成するのではなく、`CAtlException`オブジェクトに直接します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlexcept.h

##  <a name="catlexception"></a>  CAtlException::CAtlException

コンストラクターです。

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>パラメーター

*hr*<br/>
HRESULT エラー コード。

##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT

HRESULT 値を現在のオブジェクトにキャストします。

```
operator HRESULT() const throw ();
```

##  <a name="m_hr"></a>  CAtlException::m_hr

HRESULT データ メンバー。

```
HRESULT m_hr;
```

### <a name="remarks"></a>Remarks

エラー状態を格納するデータ メンバー。 HRESULT 値は、コンス トラクターによって設定[CAtlException::CAtlException](#catlexception)します。

## <a name="see-also"></a>関連項目

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
