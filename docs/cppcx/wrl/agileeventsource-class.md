---
title: AgileEventSource クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: fa1e0a72d865b2993e149f6e4d2b57fe13463a61
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821741"
---
# <a name="agileeventsource-class"></a>AgileEventSource クラス

任意のスレッドからアクセスできるコンポーネントであるアジャイルコンポーネントによって発生するイベントを表します。 [EventSource](eventsource-class.md)から継承し、`Add` メンバー関数を追加の型パラメーターでオーバーライドして、アジャイルイベントの呼び出し方法を指定します。

## <a name="syntax"></a>構文

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>パラメーター

*TDelegateInterface*<br/>
イベントハンドラーを表すデリゲートへのインターフェイス。

*TEventSourceOptions*<br/>
InvokeMode フィールドが `InvokeMode::StopOnFirstError` または `InvokeMode::FireAll`に設定されている[InvokeModeOptions](invokemodeoptions-structure.md)構造体。

## <a name="remarks"></a>Remarks

Windows ランタイムのコンポーネントの大部分はアジャイルコンポーネントです。 詳細については、「[スレッド処理C++とマーシャリング (/cx)](../../cppcx/threading-and-marshaling-c-cx.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>要件

**ヘッダー:** イベント .h

**名前空間:** Microsoft::WRL

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[AgileEventSource:: Add メソッド](#add)|指定されたデリゲートインターフェイスによって表されるアジャイルイベントハンドラーを、現在の**Agileeventsource**オブジェクトのイベントハンドラーのセットに追加します。|

## <a name="add"></a>AgileEventSource:: Add メソッド

指定されたデリゲートインターフェイスによって表されるイベントハンドラーを、現在の[EventSource](eventsource-class.md)オブジェクトのイベントハンドラーのセットに追加します。

### <a name="syntax"></a>構文

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
この操作が完了すると、イベントを表すハンドル。 このトークンを `Remove()` メソッドのパラメーターとして使用して、イベントハンドラーを破棄します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)