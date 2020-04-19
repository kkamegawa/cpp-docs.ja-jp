---
title: Platform::Object クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183210"
---
# <a name="platformobject-class"></a>Platform::Object クラス

Ref クラスと Windows ランタイム アプリで ref 構造体に対して共通の動作を提供します。 ref クラスと ref 構造体のインスタンスは、いずれも Platform::Object^ に暗黙的に変換可能で、仮想の ToString メソッドをオーバーライドできます。

## <a name="syntax"></a>構文

```cpp
public ref class Object : Object
```

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[Object::Object](#ctor)|Object クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[Object::Equals](#equals)|指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。|
|[Object::GetHashCode](#gethashcode)|このインスタンスのハッシュ コードを返します。|
|[Object::ReferenceEquals](#referenceequals)|指定された Object インスタンスが同一のインスタンスかどうかを判断します。|
|[ToString](#tostring)|現在のオブジェクトを表す文字列を返します。 オーバーライドできます。|
|[GetType](#gettype)|現在のインスタンスを記述する [Platform::Type](../cppcx/platform-type-class.md) を取得します。|

## <a name="inheritance-hierarchy"></a>継承階層

`Object`

`Object`

### <a name="requirements"></a>必要条件

**ヘッダー:** vccorlib.h

**名前空間:** プラットフォーム

## <a name="equals"></a> Object::equals メソッド

指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。

### <a name="syntax"></a>構文

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>パラメーター

*obj*<br/>
比較対象のオブジェクト。

### <a name="return-value"></a>戻り値

**true**オブジェクトが等しい場合**false**します。

## <a name="gethashcode"></a>  Object::gethashcode メソッド

COM オブジェクトの場合は、このインスタンスの `IUnknown`* ID 値を返します。COM オブジェクトでない場合は、計算済みハッシュ値を返します。

### <a name="syntax"></a>構文

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>戻り値

このオブジェクトを一意に識別する数値。

### <a name="remarks"></a>Remarks

GetHashCode を使用してマップ内のオブジェクトのキーを作成できます。 使用してハッシュ コードを比較できる[object::equals](#equals)します。 コード パスが非常に重要であるときに、`GetHashCode` と `Equals` の実行速度が不十分な場合には、基になる COM レイヤーまで移動して `IUnknown` ネイティブ ポインターの比較を実行できます。

## <a name="gettype"></a>  Object::gettype メソッド

返します、 [platform::type](../cppcx/platform-type-class.md)オブジェクトのランタイム型を記述するオブジェクト。

### <a name="syntax"></a>構文

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>プロパティ値/戻り値

A [platform::type](../cppcx/platform-type-class.md)オブジェクトのランタイム型を記述するオブジェクト。

### <a name="remarks"></a>Remarks

静的な[type::gettypecode](../cppcx/platform-type-class.md#gettypecode)を取得するために使用できる、 [platform::typecode 列挙](../cppcx/platform-typecode-enumeration.md)現在の型を表す値です。 これは主に、組み込み型に使用できます。 以外の ref クラスの型コード[platform::string](../cppcx/platform-string-class.md)オブジェクト (1) です。

[::Interop::typename](/uwp/api/windows.ui.xaml.interop.typename)クラスは、Windows コンポーネントとアプリ間で型情報を渡すことの言語に依存しない方法として Windows Api で使用されます。 T[platform::type Class](../cppcx/platform-type-class.md)間の変換演算子を持つ`Type`と`TypeName`します。

使用して、 [typeid](../extensions/typeid-cpp-component-extensions.md)演算子を返す、 `Platform::Type` XAML ページ間を移動するときなど、クラス名のオブジェクト。

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>  Object::object コンス トラクター

Object クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
public:Object();
```

## <a name="referenceequals"></a>  Object::referenceequals メソッド

指定された Object インスタンスが同一のインスタンスかどうかを判断します。

### <a name="syntax"></a>構文

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>パラメーター

*obj1*<br/>
比較する最初のオブジェクト。

*obj2*<br/>
比較する 2 番目のオブジェクト。

### <a name="return-value"></a>戻り値

**true**場合 2 つのオブジェクトは同じです。 それ以外の場合、 **false**します。

## <a name="tostring"></a>  Object::tostring メソッド (C++/CX)

現在のオブジェクトを表す文字列を返します。

### <a name="syntax"></a>構文

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>戻り値

現在のオブジェクトを表す文字列。 ref クラスまたは構造体内でカスタム文字列メッセージを表示するために、このメソッドをオーバーライドすることもできます:

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](platform-namespace-c-cx.md)<br/>
[Platform::Type クラス](platform-type-class.md)<br/>
[型システム](type-system-c-cx.md)
