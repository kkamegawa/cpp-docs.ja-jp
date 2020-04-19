---
title: unsupported_feature クラス
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 561f0a258943f6d7e1c0f1b5cae716592c931fbc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127713"
---
# <a name="unsupported_feature-class"></a>unsupported_feature クラス

サポートされていない機能が使用される場合にスローされる例外です。

## <a name="syntax"></a>構文

```cpp
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[unsupported_feature コンストラクター](#unsupported_feature)|`unsupported_feature` 例外の新しいインスタンスを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a>unsupported_feature

  `unsupported_feature` 例外の新しいインスタンスを構築します。

### <a name="syntax"></a>構文

```cpp
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明。

### <a name="return-value"></a>戻り値

`unsupported_feature` オブジェクト。

## <a name="requirements"></a>［要件］

**ヘッダー:** amprt. h

**名前空間:** Concurrency

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
