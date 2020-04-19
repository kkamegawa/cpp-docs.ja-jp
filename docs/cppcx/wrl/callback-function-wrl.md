---
title: Callback 関数 (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
ms.openlocfilehash: 10fb053ed97aaca0f4a31e3843d96aa194d8949d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821689"
---
# <a name="callback-function-wrl"></a>Callback 関数 (WRL)

メンバー関数がコールバック メソッドであるオブジェクトを作成します。

## <a name="syntax"></a>構文

```cpp
template<
   typename TDelegateInterface,
   typename TCallback
>
ComPtr<TDelegateInterface> Callback(
   TCallbackcallback
);
template<
   typename TDelegateInterface,
   typename TCallbackObject
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)()
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8,
   TArg9)
);
```

### <a name="parameters"></a>パラメーター

*TDelegateInterface*<br/>
イベントが発生したときに呼び出すデリゲートのインターフェイスを指定するテンプレート パラメーター。

*TCallback*<br/>
オブジェクトとそのコールバック メンバー関数を表すオブジェクト型を指定するテンプレート パラメーター。

*T//オブジェクト*<br/>
イベントが発生したときに呼び出されるメソッドをメンバー関数に持つオブジェクトを指定するテンプレート パラメーター。

*TArg1*<br/>
最初のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*TArg2*<br/>
2 番目のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*TArg3*<br/>
3 番目のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*TArg4*<br/>
4 番目のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*TArg5*<br/>
5 番目のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*TArg6*<br/>
6 番目のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*TArg7*<br/>
7 番目のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*TArg8*<br/>
8番目のコールバックメソッドの引数の型を指定するテンプレートパラメーター。

*TArg9*<br/>
9 番目のコールバック メソッドの引数の型を指定するテンプレート パラメーター。

*コール*<br/>
コールバック オブジェクトおよびそのメンバー関数を表すオブジェクト。

*object*<br/>
イベントが発生したときにメンバー関数が呼び出されるオブジェクト。

*method*<br/>
イベントが発生したときに呼び出すメンバー関数。

## <a name="return-value"></a>戻り値

指定されたコールバック メソッドをメンバー関数に持つオブジェクト。

## <a name="remarks"></a>Remarks

デリゲートオブジェクトの基本は、`IInspectable`ではなく `IUnknown`である必要があります。

## <a name="requirements"></a>要件

**ヘッダー:** イベント .h

**名前空間:** Microsoft::WRL

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)