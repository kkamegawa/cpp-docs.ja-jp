---
title: EventSource クラス
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: e9070fe756410e3e1bb1e5840eb3f06e29c2f46b
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336621"
---
# <a name="eventsource-class"></a>EventSource クラス

非アジャイルのイベントを表します。 `EventSource` メンバー関数は、イベント ハンドラーの追加、削除、および呼び出しを実行します。 アジャイルのイベントを使用して[AgileEventSource](agileeventsource-class.md)します。

## <a name="syntax"></a>構文

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>パラメーター

*TDelegateInterface*<br/>
イベント ハンドラーを表すデリゲートのインターフェイスです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

| 名前                                     | 説明                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource](#eventsource) | `EventSource` クラスの新しいインスタンスを初期化します。 |

### <a name="public-methods"></a>パブリック メソッド

| 名前                                 | 説明                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Add](#add)             | 現在のイベント ハンドラーのセットを指定したデリゲート インターフェイスによって表されるイベント ハンドラーを追加します。`EventSource`オブジェクト。                     |
| [EventSource::GetSize](#getsize)     | 現在関連付けられているイベント ハンドラーの数を取得`EventSource`オブジェクト。                                                                         |
| [EventSource::InvokeAll](#invokeall) | 現在関連付けられている各イベント ハンドラーを呼び出す`EventSource`オブジェクトの指定された引数の型と引数を使用します。                                      |
| [EventSource::Remove](#remove)       | 現在関連付けられているイベント ハンドラーのセットから、指定されたイベント登録トークンによって表されるイベント ハンドラーを削除します。`EventSource`オブジェクト。 |

### <a name="protected-data-members"></a>プロテクト データ メンバー

| 名前                                                    | 説明                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | アクセスを同期、 [targets _](#targets)配列を追加するときに、削除、またはイベント ハンドラーを呼び出します。                          |
| [Eventsource::targets _](#targets)                       | 1 つまたは複数のイベント ハンドラーの配列。                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | この eventsource イベントのハンドラーが追加されている場合でも、削除、または呼び出される内部データ メンバーへのアクセスを同期します。 |

## <a name="inheritance-hierarchy"></a>継承階層

`EventSource`

## <a name="requirements"></a>必要条件

**ヘッダー:** event.h

**名前空間:** Microsoft::wrl

## <a name="add"></a>EventSource::Add

現在のイベント ハンドラーのセットを指定したデリゲート インターフェイスによって表されるイベント ハンドラーを追加します。`EventSource`オブジェクト。

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>パラメーター

*delegateInterface*<br/>
イベント ハンドラーを表すデリゲート オブジェクトのインターフェイスです。

*token*<br/>
この操作の完了時、イベントを表すハンドルです。 パラメーターとしてこのトークンを使用して、 [Remove()](#remove)メソッドをイベント ハンドラーを破棄します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="addremovelock"></a>EventSource::addRemoveLock_

アクセスを同期、 [targets _](#targets)配列を追加するときに、削除、またはイベント ハンドラーを呼び出します。

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource::EventSource

`EventSource` クラスの新しいインスタンスを初期化します。

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource::GetSize

現在関連付けられているイベント ハンドラーの数を取得`EventSource`オブジェクト。

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>戻り値

内のイベント ハンドラーの数[targets _](#targets)します。

## <a name="invokeall"></a>EventSource::InvokeAll

現在関連付けられている各イベント ハンドラーを呼び出す`EventSource`オブジェクトの指定された引数の型と引数を使用します。

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>パラメーター

*T0*<br/>
0 番目のイベント ハンドラーの引数の型。

*T1*<br/>
最初のイベント ハンドラーの引数の型。

*T2*<br/>
2 番目のイベント ハンドラーの引数の型。

*T3*<br/>
3 番目のイベント ハンドラーの引数の型。

*T4*<br/>
4 番目のイベント ハンドラーの引数の型。

*T5*<br/>
5 番目のイベント ハンドラーの引数の型。

*T6*<br/>
6 番目のイベント ハンドラーの引数の型。

*T7*<br/>
7 番目のイベント ハンドラーの引数の型。

*T8*<br/>
8 番目のイベント ハンドラーの引数の型。

*T9*<br/>
9 番目のイベント ハンドラーの引数の型。

*arg0*<br/>
0 番目のイベント ハンドラーの引数。

*arg1*<br/>
最初のイベント ハンドラーの引数。

*arg2*<br/>
2 番目のイベント ハンドラーの引数。

*arg3*<br/>
3 番目のイベント ハンドラーの引数。

*arg4*<br/>
4 番目のイベント ハンドラーの引数。

*arg5*<br/>
5 番目のイベント ハンドラーの引数。

*arg6*<br/>
6 番目のイベント ハンドラーの引数。

*arg7*<br/>
7 番目のイベント ハンドラーの引数。

*arg8*<br/>
8 番目のイベント ハンドラーの引数。

*arg9*<br/>
9 番目のイベント ハンドラーの引数。

## <a name="remove"></a>EventSource::Remove

現在関連付けられているイベント ハンドラーのセットから、指定されたイベント登録トークンによって表されるイベント ハンドラーを削除します。`EventSource`オブジェクト。

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>パラメーター

*token*<br/>
イベント ハンドラーを表すハンドル。 このトークンはイベント ハンドラーの登録時に返された、 [Add()](#add)メソッド。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

詳細については、`EventRegistrationToken`構造体を参照してください、 **Windows::Foundation::EventRegistrationToken 構造**でトピック、 **Windows ランタイム**リファレンス ドキュメント。

## <a name="targets"></a>Eventsource::targets _

1 つまたは複数のイベント ハンドラーの配列。

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Remarks

ときに、現在で表されるイベント`EventSource`オブジェクトが、イベント ハンドラーは呼び出されます。

## <a name="targetspointerlock"></a>Eventsource::targetspointerlock _

このイベント ハンドラーの中にも、内部データ メンバーへのアクセスを同期`EventSource`の追加、削除、または呼び出されました。

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
