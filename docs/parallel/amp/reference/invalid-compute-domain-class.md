---
title: invalid_compute_domain クラス
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 3b8179e8e92665fa6482bd092504af71aa0106f0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126462"
---
# <a name="invalid_compute_domain-class"></a>invalid_compute_domain クラス

この例外は、ランタイムが[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)呼び出しサイトで指定された計算ドメインを使用してカーネルを起動できない場合にスローされます。

## <a name="syntax"></a>構文

```cpp
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[invalid_compute_domain コンストラクター](#ctor)|`invalid_compute_domain` クラスの新しいインスタンスを初期化します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>要件

**ヘッダー:** amprt. h

**名前空間:** Concurrency

## <a name="ctor"></a>invalid_compute_domain

クラスの新しいインスタンスを初期化します。

## <a name="syntax"></a>構文

```cpp
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明。

### <a name="return-value"></a>戻り値

`invalid_compute_domain` クラスのインスタンス。

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
