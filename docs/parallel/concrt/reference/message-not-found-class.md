---
title: message_not_found クラス
ms.date: 11/04/2016
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
ms.openlocfilehash: 63b921e47b01e3be7dfc060cbb41e5fd9016d04f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139573"
---
# <a name="message_not_found-class"></a>message_not_found クラス

このクラスは、要求されたメッセージがメッセージング ブロックで見つからない場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class message_not_found : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[message_not_found](#ctor)|オーバーロードされます。 `message_not_found` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`message_not_found`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>message_not_found

`message_not_found` オブジェクトを構築します。

```cpp
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[非同期メッセージ ブロック](../../../parallel/concrt/asynchronous-message-blocks.md)
