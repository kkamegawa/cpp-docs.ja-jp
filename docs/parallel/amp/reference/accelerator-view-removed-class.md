---
title: accelerator_view_removed クラス
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 9a3f6f349fc3103893639fe209dcf23a07ffec56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127125"
---
# <a name="accelerator_view_removed-class"></a>accelerator_view_removed クラス

基になる DirectX の呼び出しが Windows のタイムアウトの検出と回復機構が原因で失敗した場合にスローされる例外。

## <a name="syntax"></a>構文

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[accelerator_view_removed コンストラクター](#ctor)|`accelerator_view_removed` クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|`accelerator_view` オブジェクトの削除の原因を示す HRESULT エラーコードを返します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>要件

**ヘッダー:** amprt. h

**名前空間:** Concurrency

## <a name="ctor"></a>accelerator_view_removed

[Accelerator_view_removed](accelerator-view-removed-class.md)クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>パラメーター

*message*<br/>
エラーの説明。

*view_removed_reason*<br/>
`accelerator_view` オブジェクトが削除された原因を示す HRESULT エラーコード。

### <a name="return-value"></a>戻り値

`accelerator_view_removed` クラスの新しいインスタンス。

## <a name="get_view_removed_reason"></a>get_view_removed_reason

`accelerator_view` オブジェクトの削除の原因を示す HRESULT エラーコードを返します。

### <a name="syntax"></a>構文

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
