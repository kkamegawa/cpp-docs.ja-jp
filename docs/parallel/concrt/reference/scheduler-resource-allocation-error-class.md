---
title: scheduler_resource_allocation_error クラス
ms.date: 11/04/2016
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
ms.openlocfilehash: 2955320b443fb61f26d9f07ca336a45c620e2aa9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143334"
---
# <a name="scheduler_resource_allocation_error-class"></a>scheduler_resource_allocation_error クラス

このクラスは、コンカレンシー ランタイムでクリティカル リソースを取得できないためにスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|オーバーロードされます。 `scheduler_resource_allocation_error` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[get_error_code](#get_error_code)|例外の原因となったエラーコードを返します。|

## <a name="remarks"></a>解説

この例外は、通常、同時実行ランタイム内からオペレーティングシステムへの呼び出しが失敗した場合にスローされます。 通常、Win32 メソッド `GetLastError` の呼び出しから返されるエラーコードは `HRESULT` 型の値に変換され、`get_error_code` メソッドを使用して取得できます。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="get_error_code"></a>get_error_code

例外の原因となったエラーコードを返します。

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>戻り値

例外の原因となったエラーの `HRESULT` 値。

## <a name="ctor"></a>scheduler_resource_allocation_error

`scheduler_resource_allocation_error` オブジェクトを構築します。

```cpp
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

*_Hresult*<br/>
例外の原因となったエラーの `HRESULT` 値。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
