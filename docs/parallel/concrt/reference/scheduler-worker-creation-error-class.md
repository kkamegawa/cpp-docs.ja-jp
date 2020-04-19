---
title: scheduler_worker_creation_error クラス
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: e7f2763d7244be9e5e5b006b31b97c08e213a4f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142763"
---
# <a name="scheduler_worker_creation_error-class"></a>scheduler_worker_creation_error クラス

このクラスは、コンカレンシー ランタイムでワーカー実行コンテキストを作成できないためにスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|オーバーロードされます。 `scheduler_worker_creation_error` オブジェクトを構築します。|

## <a name="remarks"></a>コメント

この例外は、通常、同時実行ランタイム内から実行コンテキストを作成するためにオペレーティングシステムへの呼び出しが失敗した場合にスローされます。 実行コンテキストは、同時実行ランタイムでタスクを実行するスレッドです。 通常、Win32 メソッド `GetLastError` の呼び出しから返されるエラーコードは `HRESULT` 型の値に変換され、基本クラスのメソッド `get_error_code`を使用して取得できます。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>scheduler_worker_creation_error

`scheduler_worker_creation_error` オブジェクトを構築します。

```cpp
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

*_Hresult*<br/>
例外の原因となったエラーの `HRESULT` 値。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
