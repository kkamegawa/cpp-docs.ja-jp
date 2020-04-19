---
title: HANDLENullTraits 構造体
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: d70425f414b998eb67e3937c2c126dd3eda0c00d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398382"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 構造体

初期化されていないハンドルの一般的な特性を定義します。

## <a name="syntax"></a>構文

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前   | 説明
------ | ---------------------
`Type` | ハンドルのシノニムです。

### <a name="public-methods"></a>パブリック メソッド

名前                                                  | 説明
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Close](#close)                     | 指定したハンドルを閉じます。
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | 無効なハンドルを表します。

## <a name="inheritance-hierarchy"></a>継承階層

`HANDLENullTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLENullTraits::Close

指定したハンドルを閉じます。

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
ハンドルを閉じます。

### <a name="return-value"></a>戻り値

**true**場合処理*h*正常。 それ以外の終了**false**します。

## <a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

無効なハンドルを表します。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>戻り値

常に `nullptr` を返します。
