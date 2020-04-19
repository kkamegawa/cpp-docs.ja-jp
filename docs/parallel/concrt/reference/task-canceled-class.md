---
title: task_canceled クラス
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: b1436f921343843ee2b50888f00b6d470e513329
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142606"
---
# <a name="task_canceled-class"></a>task_canceled クラス

このクラスは、現在のタスクを強制的に取り消すために PPL タスク レイヤーによってスローされる例外を表します。 取り消されたタスクについては、[タスク](/visualstudio/extensibility/debugger/task-class-internal-members)の `get()` メソッドによってもスローされます。

## <a name="syntax"></a>構文

```cpp
class task_canceled : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[task_canceled](#ctor)|オーバーロードされます。 `task_canceled` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`task_canceled`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>task_canceled

`task_canceled` オブジェクトを構築します。

```cpp
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
