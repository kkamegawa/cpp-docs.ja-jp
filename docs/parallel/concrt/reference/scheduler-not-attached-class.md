---
title: scheduler_not_attached クラス
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: a3b1c113e5c6c5feb5b2fa1940ee9b984233e4af
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142205"
---
# <a name="scheduler_not_attached-class"></a>scheduler_not_attached クラス

このクラスは、現在のコンテキストにスケジューラがアタッチされている必要がある操作を実行するときにスケジューラがアタッチされていない場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|オーバーロードされます。 `scheduler_not_attached` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>scheduler_not_attached

`scheduler_not_attached` オブジェクトを構築します。

```cpp
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[Scheduler クラス](scheduler-class.md)
