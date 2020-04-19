---
title: missing_wait クラス
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: cf81d1ee6c144da210da5b1f37aca7910ae37bc8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142386"
---
# <a name="missing_wait-class"></a>missing_wait クラス

このクラスは、`task_group` オブジェクトまたは `structured_task_group` オブジェクトのデストラクターの実行時に、そのオブジェクトにスケジュールされたタスクがまだ存在する場合にスローされる例外を表します。 例外の結果としてのスタック アンワインドによりデストラクターが実行される場合、この例外はスローされません。

## <a name="syntax"></a>構文

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[missing_wait](#ctor)|オーバーロードされます。 `missing_wait` オブジェクトを構築します。|

## <a name="remarks"></a>解説

例外フローが存在しない場合は、オブジェクトの破棄を許可する前に、`task_group` または `structured_task_group` オブジェクトの `wait` または `run_and_wait` メソッドを呼び出す必要があります。 ランタイムは、`wait` または `run_and_wait` メソッドの呼び出しを忘れたことを示すために、この例外をスローします。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`missing_wait`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>missing_wait

`missing_wait` オブジェクトを構築します。

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[task_group クラス](task-group-class.md)<br/>
[待機](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group クラス](structured-task-group-class.md)
