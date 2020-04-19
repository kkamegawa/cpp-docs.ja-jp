---
title: nested_scheduler_missing_detach クラス
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: 8c9553b036890c4ce28f1060bfe2f58ee1904935
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138867"
---
# <a name="nested_scheduler_missing_detach-class"></a>nested_scheduler_missing_detach クラス

このクラスは、`CurrentScheduler::Detach` オブジェクトの `Attach` メソッドによって別のスケジューラにアタッチされているコンテキストで `Scheduler` メソッドが呼び出されなかったことを、コンカレンシー ランタイムが検出した場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|オーバーロードされます。 `nested_scheduler_missing_detach` オブジェクトを構築します。|

## <a name="remarks"></a>コメント

この例外がスローされるのは、別のスケジューラに既に所有されているか、別のスケジューラにアタッチされているコンテキストで `Scheduler` オブジェクトの `Attach` メソッドを呼び出すことによって、スケジューラを別の内部に入れ子にした場合のみです。 同時実行ランタイムは、問題を特定するための支援としてシナリオを検出できる場合に、この例外させるをスローします。 `CurrentScheduler::Detach` メソッドを呼び出すための怠りのすべてのインスタンスが、この例外をスローすることは保証されていません。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>nested_scheduler_missing_detach

`nested_scheduler_missing_detach` オブジェクトを構築します。

```cpp
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[Scheduler クラス](scheduler-class.md)
