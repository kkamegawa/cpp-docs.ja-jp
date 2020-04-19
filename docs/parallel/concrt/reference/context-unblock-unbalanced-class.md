---
title: context_unblock_unbalanced クラス
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: 261ec96c1a83fbec423e6dbbfe403c4db53a2962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143094"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced クラス

このクラスは、`Block` オブジェクトの `Unblock` メソッドと `Context` メソッドの呼び出しが正しく対になっていない場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|オーバーロードされます。 `context_unblock_unbalanced` オブジェクトを構築します。|

## <a name="remarks"></a>解説

`Context` オブジェクトの `Block` および `Unblock` メソッドの呼び出しは、常に適切にペアになっている必要があります。 同時実行ランタイムでは、いずれかの順序で操作を実行できます。 たとえば、`Block` の呼び出しの後に、`Unblock`を呼び出すか、その逆を行うことができます。 たとえば、`Unblock` メソッドに対する2回の呼び出しが、ブロックされていない `Context` オブジェクトで行に作成された場合に、この例外がスローされます。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>context_unblock_unbalanced

`context_unblock_unbalanced` オブジェクトを構築します。

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
