---
title: __RTDynamicCast
ms.date: 11/04/2016
api_name:
- __RTDynamicCast
api_location:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: c4b0caadf20d6c5494acf47ee5a788b5ee009c47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957334"
---
# <a name="__rtdynamiccast"></a>__RTDynamicCast

[dynamic_cast](../cpp/dynamic-cast-operator.md) 演算子のランタイム実装です。

## <a name="syntax"></a>構文

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>パラメーター

*inptr*<br/>
ポリモーフィック型オブジェクトへのポインター。

*VfDelta*<br/>
オブジェクト内の仮想関数ポインターのオフセット。

*SrcType*<br/>
`inptr` パラメーターでポイントするオブジェクトのスタティック型。

*TargetType*<br/>
キャストの意図した結果。

*isReference*<br/>
入力が参照の場合は **true**、ポインターの場合は **false**。

## <a name="return-value"></a>戻り値

成功した場合は適切なサブオブジェクトへのポインター、それ以外の場合は **NULL**。

## <a name="exceptions"></a>例外

`dynamic_cast<>` への入力が参照でありキャストに失敗した場合は `bad_cast()`。

## <a name="remarks"></a>解説

`inptr` を `TargetType` 型のオブジェクトに変換します。 `inptr` の型は、`TargetType` がポインターの場合はポインター、`TargetType` が参照の場合は左辺値である必要があります。 `TargetType` は、以前に定義されたクラス型への参照かポインター、または void 型へのポインターである必要があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|