---
title: improper_lock クラス
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: 886444f3e856234be010715a8ee0c707cf919bb4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142395"
---
# <a name="improper_lock-class"></a>improper_lock クラス

このクラスは、ロックが正しく取得されなかった場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class improper_lock : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[improper_lock](#ctor)|オーバーロードされます。 `improper_lock exception` を構築します。|

## <a name="remarks"></a>解説

通常、この例外は、同じコンテキストで再入不可能なロックを再帰的に取得しようとしたときにスローされます。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`improper_lock`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>improper_lock

`improper_lock exception` を構築します。

```cpp
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[critical_section クラス](critical-section-class.md)<br/>
[reader_writer_lock クラス](reader-writer-lock-class.md)
