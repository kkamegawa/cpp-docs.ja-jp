---
title: bad_target クラス
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 023607ff142b7fa39165cc9b5280a8e9345a3645
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142856"
---
# <a name="bad_target-class"></a>bad_target クラス

このクラスは、実行する操作の無効なターゲットへのポインターがメッセージング ブロックに渡された場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[bad_target](#ctor)|オーバーロードされます。 `bad_target` オブジェクトを構築します。|

## <a name="remarks"></a>コメント

この例外は、通常、ターゲットが別のターゲット用に予約されているメッセージを使用しようとした場合や、保持していない予約を解除しようとした場合にスローされます。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`bad_target`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>bad_target

`bad_target` オブジェクトを構築します。

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[非同期メッセージ ブロック](../../../parallel/concrt/asynchronous-message-blocks.md)
