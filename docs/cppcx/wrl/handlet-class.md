---
title: HandleT クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: f66fbe23c305be15e09928242175dfa7ce8c141b
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821819"
---
# <a name="handlet-class"></a>HandleT クラス

オブジェクトへのハンドルを表します。

## <a name="syntax"></a>構文

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>パラメーター

*HandleTraits*<br/>
ハンドルの共通特性を定義する[handletraits](handletraits-structure.md)構造体のインスタンス。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

[名前]     | 説明
-------- | -----------------------------
`Traits` | `HandleTraits` と同義。

### <a name="public-constructors"></a>パブリック コンストラクター

[名前]                                | 説明
----------------------------------- | --------------------------------------------------
[ハンドラー Let:: ハンドラー Let](#handlet)        | `HandleT` クラスの新しいインスタンスを初期化します。
[ハンドラーの Let:: ~ の実行](#tilde-handlet) | `HandleT` クラスのインスタンスを初期化解除します。

### <a name="public-methods"></a>パブリック メソッド

[名前]                         | 説明
---------------------------- | ----------------------------------------------------------------------
[実行の許可:: Attach](#attach)   | 指定したハンドルを現在の `HandleT` オブジェクトに関連付けます。
[実行の許可:: 閉じる](#close)     | 現在の `HandleT` オブジェクトを閉じます。
[使用方法::D etach](#detach)   | 現在の `HandleT` オブジェクトと基になるハンドルとの関連付けを解除します。
[Get-help Let:: Get](#get)         | 基になるハンドルの値を取得します。
[Let let:: IsValid](#isvalid) | 現在の `HandleT` オブジェクトがハンドルを表しているかどうかを示します。

### <a name="protected-methods"></a>プロテクト メソッド

[名前]                                     | 説明
---------------------------------------- | ------------------------------------
[ハンドラー Let:: InternalClose](#internalclose) | 現在の `HandleT` オブジェクトを閉じます。

### <a name="public-operators"></a>パブリック演算子

[名前]                                   | 説明
-------------------------------------- | ----------------------------------------------------------------------------------
[Let let:: operator =](#operator-assign) | 指定された `HandleT` オブジェクトの値を現在の `HandleT` オブジェクトに移動します。

### <a name="protected-data-members"></a>保護されるデータ メンバー

[名前]                        | 説明
--------------------------- | ----------------------------------------------------------------
[使用方法:: handle_](#handle) | `HandleT` オブジェクトによって表されるハンドルを格納します。

## <a name="inheritance-hierarchy"></a>継承階層

`HandleT`

## <a name="requirements"></a>要件

**ヘッダー:** corewrappers .h

**名前空間:** Microsoft:: WRL:: Wrapper

## <a name="tilde-handlet"></a>ハンドラーの Let:: ~ の実行

`HandleT` クラスのインスタンスを初期化解除します。

```cpp
~HandleT();
```

## <a name="attach"></a>実行の許可:: Attach

指定したハンドルを現在の `HandleT` オブジェクトに関連付けます。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
ハンドル。

## <a name="close"></a>実行の許可:: 閉じる

現在の `HandleT` オブジェクトを閉じます。

```cpp
void Close();
```

### <a name="remarks"></a>コメント

現在の `HandleT` の基になるハンドルが閉じられ、`HandleT` が無効な状態に設定されています。

ハンドルが正常に終了しない場合は、呼び出し元のスレッドで例外が発生します。

## <a name="detach"></a>使用方法::D etach

現在の `HandleT` オブジェクトと基になるハンドルとの関連付けを解除します。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>戻り値

基になるハンドル。

### <a name="remarks"></a>コメント

この操作が完了すると、現在の `HandleT` は無効な状態に設定されます。

## <a name="get"></a>Get-help Let:: Get

基になるハンドルの値を取得します。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>戻り値

ハンドル。

## <a name="handle"></a>使用方法:: handle_

`HandleT` オブジェクトによって表されるハンドルを格納します。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>ハンドラー Let:: ハンドラー Let

`HandleT` クラスの新しいインスタンスを初期化します。

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
ハンドル。

### <a name="remarks"></a>コメント

最初のコンストラクターは、オブジェクトに対する有効なハンドルではない `HandleT` オブジェクトを初期化します。 2番目のコンストラクターは、パラメーター *h*から新しい `HandleT` オブジェクトを作成します。

## <a name="internalclose"></a>ハンドラー Let:: InternalClose

現在の `HandleT` オブジェクトを閉じます。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>戻り値

現在の `HandleT` 正常に閉じられた場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>コメント

`InternalClose()` は `protected`です。

## <a name="isvalid"></a>Let let:: IsValid

現在の `HandleT` オブジェクトがハンドルを表しているかどうかを示します。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>戻り値

`HandleT` がハンドルを表している場合は**true** 。それ以外の場合は**false**。

## <a name="operator-assign"></a>Let let:: operator =

指定された `HandleT` オブジェクトの値を現在の `HandleT` オブジェクトに移動します。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
ハンドルへの右辺値参照。

### <a name="return-value"></a>戻り値

現在の `HandleT` オブジェクトへの参照。

### <a name="remarks"></a>コメント

この操作では、parameter *h*によって指定された `HandleT` オブジェクトを無効にします。
