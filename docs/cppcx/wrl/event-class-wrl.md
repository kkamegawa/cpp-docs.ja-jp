---
title: イベント クラス (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 2d36b4fa3d1824f43e0cfafe55c439a6bdeccb6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398551"
---
# <a name="event-class-wrl"></a>イベント クラス (WRL)

イベントを表します。

## <a name="syntax"></a>構文

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                   | 説明
---------------------- | ------------------------------------------------
[Event::event](#event) | `Event` クラスの新しいインスタンスを初期化します。

### <a name="public-operators"></a>パブリック演算子

名前                                 | 説明
------------------------------------ | ------------------------------------------------------------------------
[Event::operator =](#operator-assign) | 指定した割り当て`Event`現在への参照を`Event`インスタンス。

## <a name="inheritance-hierarchy"></a>継承階層

`HandleT`

`Event`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers

## <a name="event"></a>Event::event

`Event` クラスの新しいインスタンスを初期化します。

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
イベントに対するハンドル。 既定では、 *h*に初期化されます`nullptr`します。

## <a name="operator-assign"></a>Event::operator =

指定した割り当て`Event`現在への参照を`Event`インスタンス。

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
右辺値参照を`Event`インスタンス。

### <a name="return-value"></a>戻り値

現在へのポインター`Event`インスタンス。
