---
title: DeferrableEventArgs クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: 4a3786e65873d6837389ad4fa5e7d06a14d66460
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398577"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs クラス

遅延のイベント引数の型に使用されるテンプレート クラス。

## <a name="syntax"></a>構文

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>パラメーター

*TEventArgsInterface*<br/>
遅延イベントの引数を宣言するインターフェイスの型。

*TEventArgsClass*<br/>
実装するクラス*TEventArgsInterface*します。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

名前                                                         | 説明
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[Deferrableeventargs::getdeferral](#getdeferral)             | 参照を取得、[遅延](/uwp/api/windows.foundation.deferral)遅延イベントを表すオブジェクト。
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | 遅延イベントを処理するすべての処理が完了したことを示すために呼び出されます。

## <a name="remarks"></a>Remarks

このクラスのインスタンスは、遅延イベントのイベント ハンドラーに渡されます。 テンプレート パラメーターは、遅延イベントの特定の種類のイベント引数の詳細を定義するインターフェイスと、そのインターフェイスを実装するクラスを表します。

クラスは遅延イベントのイベント ハンドラーの最初の引数として表示されます。 呼び出すことができます、 [GetDeferral](#getdeferral)を取得するメソッド、[遅延](/uwp/api/windows.foundation.deferral)遅延イベントに関するすべての情報を表示するオブジェクト。 イベント処理を完了した後、遅延オブジェクトで Complete を呼び出す必要があります。 呼び出す必要がありますし、 [InvokeAllFinished](#invokeallfinished)イベント ハンドラー メソッドの末尾には、保証すべて遅延イベントの完了が正しく伝達されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** event.h

**名前空間:** Microsoft::wrl

## <a name="getdeferral"></a>Deferrableeventargs::getdeferral

参照を取得、[遅延](/uwp/api/windows.foundation.deferral)遅延イベントを表すオブジェクト。

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>パラメーター

*結果*<br/>
参照するポインター、[遅延](/uwp/api/windows.foundation.deferral)呼び出しの完了時のオブジェクトします。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="invokeallfinished"></a>Deferrableeventargs::invokeallfinished

遅延イベントを処理するすべての処理が完了したことを示すために呼び出されます。

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Remarks

イベント ソース呼び出しの後にこのメソッドを呼び出す必要があります[InvokeAll](eventsource-class.md#invokeall)します。 このメソッドを呼び出すことで、さらに遅延が取られることを回避し、遅延が取られなかった場合は、完了ハンドラーの実行を強制します。
