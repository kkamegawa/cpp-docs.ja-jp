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
ms.openlocfilehash: 1350e51ff609a888b6a8ad6841be6856b68c7994
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821832"
---
# <a name="eventsource-class"></a>EventSource クラス

非アジャイルイベントを表します。 `EventSource` メンバー関数は、イベント ハンドラーの追加、削除、および呼び出しを実行します。 アジャイルイベントの場合は、 [Agileeventsource](agileeventsource-class.md)を使用します。

## <a name="syntax"></a>構文

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>パラメーター

*TDelegateInterface*<br/>
イベントハンドラーを表すデリゲートへのインターフェイス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

| [名前]                                     | 説明                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource](#eventsource) | `EventSource` クラスの新しいインスタンスを初期化します。 |

### <a name="public-methods"></a>パブリック メソッド

| [名前]                                 | 説明                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Add](#add)             | 指定されたデリゲートインターフェイスによって表されるイベントハンドラーを、現在の `EventSource` オブジェクトのイベントハンドラーのセットに追加します。                     |
| [EventSource:: GetSize](#getsize)     | 現在の `EventSource` オブジェクトに関連付けられているイベントハンドラーの数を取得します。                                                                         |
| [EventSource:: InvokeAll](#invokeall) | 指定された引数の型および引数を使用して、現在の `EventSource` オブジェクトに関連付けられている各イベントハンドラーを呼び出します。                                      |
| [EventSource::Remove](#remove)       | 現在の `EventSource` オブジェクトに関連付けられている一連のイベントハンドラーから、指定したイベント登録トークンによって表されるイベントハンドラーを削除します。 |

### <a name="protected-data-members"></a>保護されるデータ メンバー

| [名前]                                                    | 説明                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | イベントハンドラーを追加、削除、または呼び出すときに、 [targets_](#targets)配列へのアクセスを同期します。                          |
| [EventSource:: targets_](#targets)                       | 1つ以上のイベントハンドラーの配列。                                                                                           |
| [EventSource:: targetsPointerLock_](#targetspointerlock) | この EventSource のイベントハンドラーが追加、削除、または呼び出されている間でも、内部データメンバーへのアクセスを同期します。 |

## <a name="inheritance-hierarchy"></a>継承階層

`EventSource`

## <a name="requirements"></a>要件

**ヘッダー:** イベント .h

**名前空間:** Microsoft::WRL

## <a name="add"></a>EventSource::Add

指定されたデリゲートインターフェイスによって表されるイベントハンドラーを、現在の `EventSource` オブジェクトのイベントハンドラーのセットに追加します。

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>パラメーター

*delegateInterface*<br/>
イベントハンドラーを表すデリゲートオブジェクトへのインターフェイス。

*token*<br/>
この操作が完了すると、イベントを表すハンドル。 このトークンを[Remove ()](#remove)メソッドのパラメーターとして使用して、イベントハンドラーを破棄します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="addremovelock"></a>EventSource:: addRemoveLock_

イベントハンドラーを追加、削除、または呼び出すときに、 [targets_](#targets)配列へのアクセスを同期します。

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource::EventSource

`EventSource` クラスの新しいインスタンスを初期化します。

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource:: GetSize

現在の `EventSource` オブジェクトに関連付けられているイベントハンドラーの数を取得します。

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>戻り値

[Targets_](#targets)内のイベントハンドラーの数。

## <a name="invokeall"></a>EventSource:: InvokeAll

指定された引数の型および引数を使用して、現在の `EventSource` オブジェクトに関連付けられている各イベントハンドラーを呼び出します。

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
取り出しイベントハンドラーの引数の型。

*T1*<br/>
最初のイベントハンドラー引数の型。

*T2*<br/>
2番目のイベントハンドラー引数の型。

*T3*<br/>
3番目のイベントハンドラー引数の型。

*T4*<br/>
4番目のイベントハンドラー引数の型。

*T5*<br/>
5番目のイベントハンドラー引数の型。

*T6*<br/>
6番目のイベントハンドラー引数の型。

*T7*<br/>
7番目のイベントハンドラー引数の型。

*T8*<br/>
8番目のイベントハンドラー引数の型。

*T9*<br/>
9番目のイベントハンドラー引数の型。

*arg0*<br/>
取り出しイベントハンドラーの引数。

*arg1*<br/>
最初のイベントハンドラー引数。

*引数*<br/>
2番目のイベントハンドラー引数。

*arg3*<br/>
3番目のイベントハンドラー引数。

*arg4*<br/>
4番目のイベントハンドラー引数。

*arg5*<br/>
5番目のイベントハンドラー引数。

*arg6*<br/>
6番目のイベントハンドラー引数。

*arg7*<br/>
7番目のイベントハンドラー引数。

*arg8*<br/>
8番目のイベントハンドラー引数。

*arg9*<br/>
9番目のイベントハンドラー引数。

## <a name="remove"></a>EventSource::Remove

現在の `EventSource` オブジェクトに関連付けられている一連のイベントハンドラーから、指定したイベント登録トークンによって表されるイベントハンドラーを削除します。

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>パラメーター

*token*<br/>
イベントハンドラーを表すハンドル。 このトークンは、イベントハンドラーが[Add ()](#add)メソッドによって登録されたときに返されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>コメント

`EventRegistrationToken` 構造体の詳細については、 **Windows ランタイム**リファレンスドキュメントの「 **Windows:: Foundation:: EventRegistrationToken structure** 」を参照してください。

## <a name="targets"></a>EventSource:: targets_

1つ以上のイベントハンドラーの配列。

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>コメント

現在の `EventSource` オブジェクトによって表されるイベントが発生すると、イベントハンドラーが呼び出されます。

## <a name="targetspointerlock"></a>EventSource:: targetsPointerLock_

この `EventSource` のイベントハンドラーが追加、削除、または呼び出されている場合でも、内部データメンバーへのアクセスを同期します。

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
