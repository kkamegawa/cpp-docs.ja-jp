---
title: EventTargetArray クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 1f3f8e299dba1f4b6ae5a5767f11989dc2fe8370
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398486"
---
# <a name="eventtargetarray-class"></a>EventTargetArray クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Remarks

イベント ハンドラーの配列を表します。

関連付けられているイベント ハンドラー、 [EventSource](eventsource-class.md)オブジェクトが格納されている保護されたで`EventTargetArray`データ メンバー。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                           | 説明
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | `EventTargetArray` クラスの新しいインスタンスを初期化します。
[EventTargetArray:: ~ EventTargetArray](#tilde-eventtargetarray) | 現在の初期化を解除`EventTargetArray`クラス。

### <a name="public-methods"></a>パブリック メソッド

名前                                  | 説明
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | イベント ハンドラーの内部配列の末尾には、指定したイベント ハンドラーを追加します。
[Eventtargetarray::begin](#begin)     | イベント ハンドラーの内部配列の最初の要素のアドレスを取得します。
[Eventtargetarray::end](#end)         | イベント ハンドラーの内部配列の最後の要素のアドレスを取得します。
[EventTargetArray::Length](#length)   | イベント ハンドラーの内部配列の要素の現在の数を取得します。

## <a name="inheritance-hierarchy"></a>継承階層

`EventTargetArray`

## <a name="requirements"></a>必要条件

**ヘッダー:** event.h

**名前空間:** Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray:: ~ EventTargetArray

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Remarks

現在の初期化を解除`EventTargetArray`クラス。

## <a name="addtail"></a>EventTargetArray::AddTail

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>パラメーター

*要素*<br/>
追加するイベント ハンドラーへのポインター。

### <a name="remarks"></a>Remarks

イベント ハンドラーの内部配列の末尾には、指定したイベント ハンドラーを追加します。

`AddTail()` 内部でのみ使用するものでは、`EventSource`クラス。

## <a name="begin"></a>Eventtargetarray::begin

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>戻り値

イベント ハンドラーの内部配列の最初の要素のアドレス。

### <a name="remarks"></a>Remarks

イベント ハンドラーの内部配列の最初の要素のアドレスを取得します。

## <a name="end"></a>Eventtargetarray::end

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>戻り値

イベント ハンドラーの内部配列の最後の要素のアドレス。

### <a name="remarks"></a>Remarks

イベント ハンドラーの内部配列の最後の要素のアドレスを取得します。

## <a name="eventtargetarray"></a>Eventtargetarray::eventtargetarray

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>パラメーター

*hr*<br/>
このコンス トラクター操作後にパラメーター *hr*配列の割り当てが成功または失敗するかどうかを示します。 次の一覧は、可能な値を示しています。 *hr*します。

+   S_OK<br/>
    操作が成功しました。

+   E_OUTOFMEMORY<br/>
    配列にメモリを割り当てできませんでした。

+   S_FALSE<br/>
    パラメーター*項目*が 0 未満です。

*項目*<br/>
割り当てる配列要素の数。

### <a name="remarks"></a>Remarks

`EventTargetArray` クラスの新しいインスタンスを初期化します。

`EventTargetArray` 配列内のイベント ハンドラーを保持するために使用する`EventSource`オブジェクト。

## <a name="length"></a>EventTargetArray::Length

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
size_t Length();
```

### <a name="return-value"></a>戻り値

イベント ハンドラーの内部配列の要素の現在数。

### <a name="remarks"></a>Remarks

イベント ハンドラーの内部配列の要素の現在の数を取得します。
