---
title: Platform::Box クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: ca8c9229d0ef5fa654f462282f257b1684984102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404651"
---
# <a name="platformbox-class"></a>Platform::Box クラス

`Windows::Foundation::DateTime` などの値型または `int` などのスカラー型を `Platform::Object` 型に格納できるようにします。 通常は、 `Box` を明示的に使用する必要はありません。これは、値型を `Object^`にキャストすると、ボックス化が暗黙的に発生するためです。

### <a name="syntax"></a>構文

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>必要条件

**ヘッダー:** vccorlib.h

**名前空間:** プラットフォーム

### <a name="members"></a>メンバー

|メンバー|説明|
|------------|-----------------|
|[Box](#ctor) | 指定された型の値をカプセル化する `Box` を作成します。 |
|[演算子ボックス&lt;const T&gt;^](#box-const-t) | `const` 値クラスの `T` または `enum` クラスの `T` から `Box<T>` へのボックス化変換を有効にします。 |
|[演算子ボックス&lt;const volatile T&gt;^](#box-const-volatile-t) | `const volatile` 値クラスの `T` または `enum` 型の `T` から `Box<T>` へのボックス化変換を有効にします。 |
|[演算子ボックス&lt;T&gt;^](#box-t) | 値クラス `T` から `Box<T>` へのボックス化変換を有効にします。 |
|[演算子ボックス&lt;揮発性 T&gt;^](#box-volatile-t) | `volatile` 値クラスの `T` または `enum` 型の `T` から `Box<T>` へのボックス化変換を有効にします。 |
|[Box::operator T](#t) | 値クラス `T` または `enum` クラスの `T` から `Box<T>` へのボックス化変換を有効にします。 |
|[Value プロパティ](#value) | `Box` オブジェクトにカプセル化された値を返します。 |

## <a name="ctor"></a> Box::box コンス トラクター

指定された型の値をカプセル化する `Box` を作成します。

### <a name="syntax"></a>構文

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>パラメーター

*valueArg*<br/>
ボックス化される値の型 (たとえば、`int`、`bool`、`float64`、`DateTime`。)

## <a name="box-const-t"></a> Box::operator Box&lt;const T&gt;^ 演算子

`const` 値クラスの `T` または `enum` クラスの `T` から `Box<T>` へのボックス化変換を有効にします。

### <a name="syntax"></a>構文

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
値クラス、値構造体、または列挙型。 組み込み型が含まれています、[既定の名前空間](../cppcx/default-namespace.md)します。

### <a name="return-value"></a>戻り値

A `Platform::Box<T>^` ref クラスでボックス化された元の値を表すインスタンス。

## <a name="box-const-volatile-t"></a> Box::operator Box&lt;const volatile T&gt;^ 演算子

`const volatile` 値クラスの `T` または `enum` 型の `T` から `Box<T>` へのボックス化変換を有効にします。

### <a name="syntax"></a>構文

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
列挙型、値クラス、または値構造体。 組み込み型が含まれています、[既定の名前空間](../cppcx/default-namespace.md)します。

### <a name="return-value"></a>戻り値

A `Platform::Box<T>^` ref クラスでボックス化された元の値を表すインスタンス。

## <a name="box-t"></a> Box::operator Box&lt;T&gt;^ 演算子

値クラス `T` から `Box<T>` へのボックス化変換を有効にします。

### <a name="syntax"></a>構文

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
列挙型、値クラス、または値構造体。 組み込み型が含まれています、[既定の名前空間](../cppcx/default-namespace.md)します。

### <a name="return-value"></a>戻り値

A `Platform::Box<T>^` ref クラスでボックス化された元の値を表すインスタンス。

## <a name="box-volatile-t"></a> Box::operator Box&lt;揮発性 T&gt;^ 演算子

`volatile` 値クラスの `T` または `enum` 型の `T` から `Box<T>` へのボックス化変換を有効にします。

### <a name="syntax"></a>構文

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
列挙型、値クラス、または値構造体。 組み込み型が含まれています、[既定の名前空間](../cppcx/default-namespace.md)します。

### <a name="return-value"></a>戻り値

A `Platform::Box<T>^` ref クラスでボックス化された元の値を表すインスタンス。

## <a name="t"></a>  Box::operator T 演算子

値クラス `T` または `enum` クラスの `T` から `Box<T>` へのボックス化変換を有効にします。

### <a name="syntax"></a>構文

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
列挙型、値クラス、または値構造体。 組み込み型が含まれています、[既定の名前空間](../cppcx/default-namespace.md)します。

### <a name="return-value"></a>戻り値

A `Platform::Box<T>^` ref クラスでボックス化された元の値を表すインスタンス。

## <a name="value"></a> Box::value プロパティ

`Box` オブジェクトにカプセル化された値を返します。

### <a name="syntax"></a>構文

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>戻り値

値がボックス化される前と同じ型のボックス化された値を返します。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)<br/>
[ボックス化](../cppcx/boxing-c-cx.md)
