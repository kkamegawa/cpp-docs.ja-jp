---
title: Platform::Agile クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 86a535bc106e17b276dc5f42a59773aa0de8c361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161668"
---
# <a name="platformagile-class"></a>Platform::Agile クラス

アジャイル オブジェクトとして MashalingBehavior=Standard を含むオブジェクトを表します。これはランタイム スレッドの例外の頻度を大幅に減らします。 `Agile<T>` を使うと、非アジャイル オブジェクトによる同じスレッドや別のスレッドの呼び出しや、同じスレッドや別のスレッドによる非アジャイル オブジェクトの呼び出しができるようになります。 詳細については、次を参照してください。[スレッドとマーシャ リング](../cppcx/threading-and-marshaling-c-cx.md)します。

## <a name="syntax"></a>構文

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
非アジャイル クラスの型名です。

### <a name="remarks"></a>Remarks

ほとんどの Windows ランタイム クラスはアジャイルです。 アジャイル オブジェクトは、同じスレッドまたは別のスレッドのインプロセスまたはアウトプロセス オブジェクトを呼び出すことができます。また、同じスレッドまたは別のスレッドのインプロセスまたはアウトプロセス オブジェクトから呼び出されることもできます。 オブジェクトがアジャイルでない場合、非アジャイル オブジェクトをアジャイルである `Agile<T>` オブジェクトにラップします。 その後、 `Agile<T>` オブジェクトをマーシャリングしたり、基になる非アジャイル オブジェクトを使ったりできるようになります。

`Agile<T>` クラスはネイティブな標準 C++ クラスであり、 `agile.h`が必要です。 これは、非アジャイル オブジェクトと、Agile オブジェクトの *コンテキスト*を表します。 コンテキストは、アジャイル オブジェクトのスレッド モデルとマーシャリング動作を指定します。 オペレーティング システムは、コンテキストを使って、オブジェクトをマーシャリングする方法を決定します。

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[Agile::agile](#ctor)|アジャイル クラスの新しいインスタンスを初期化します。|
|[Agile::~Agile デストラクター](#dtor)|Agile クラスの現在のインスタンスを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[Agile::Get](#get)|現在の Agile オブジェクトによって表されるオブジェクトへのハンドルを返します。|
|[Agile::GetAddressOf](#getaddressof)|現在の Agile オブジェクトを再初期化し、 `T`型のオブジェクトへのハンドルのアドレスを返します。|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|現在の Agile オブジェクトによって表されるオブジェクトへのハンドルのアドレスを返します。|
|[Agile::Release](#release)|現在の Agile オブジェクトの基になるオブジェクトとコンテキストを破棄します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[Agile::operator->](#operator-arrow)|現在の Agile オブジェクトによって表されるオブジェクトへのハンドルを取得します。|
|[Agile::operator=](#operator-assign)|指定された値を現在の Agile オブジェクトに割り当てます。|

## <a name="inheritance-hierarchy"></a>継承階層

`Object`

`Agile`

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**ヘッダー:** agile.h

## <a name="ctor"></a>  Agile::agile コンス トラクター

アジャイル クラスの新しいインスタンスを初期化します。

## <a name="syntax"></a>構文

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型名パラメーターで指定される型。

*object*<br/>
このコンストラクターの 2 番目のバージョンでは、新しいアジャイル インスタンスを初期化するために使用されるオブジェクト。 3 番目のバージョンでは、新しいアジャイル インスタンスにコピーされるオブジェクト。 4 番目のバージョンでは、新しいアジャイル インスタンスに移動されるオブジェクト。

### <a name="remarks"></a>Remarks

このコンストラクターの最初のバージョンは、既定のコンストラクターです。 2 番目のバージョンは、`object` パラメーターで指定されたオブジェクトから新しいアジャイル インスタンス クラスを初期化します。 3 番目のバージョンは、コピー コンストラクターです。 4 番目のバージョンは、移動コンストラクターです。 このコンストラクターは例外をスローできません。

## <a name="dtor"></a>  Agile:: ~ Agile デストラクター

Agile クラスの現在のインスタンスを破棄します。

## <a name="syntax"></a>構文

```cpp
~Agile();
```

### <a name="remarks"></a>Remarks

このデストラクターは、現在の Agile オブジェクトによって表されるオブジェクトも解放します。

## <a name="get"></a>   Agile::get メソッド

現在の Agile オブジェクトによって表されるオブジェクトへのハンドルを返します。

## <a name="syntax"></a>構文

```cpp
T^ Get() const;
```

### <a name="return-value"></a>戻り値

現在の Agile オブジェクトによって表されるオブジェクトへのハンドル。

戻り値の型は、実際には非公開の内部型です。 戻り値を保持する便利な方法で宣言された変数に割り当てるには、**自動**推論キーワードを入力します。 たとえば、`auto x = myAgileTvariable->Get();` のようにします。

## <a name="getaddressof"></a>  Agile::getaddressof メソッド

現在の Agile オブジェクトを再初期化し、 `T`型のオブジェクトへのハンドルのアドレスを返します。

## <a name="syntax"></a>構文

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型名パラメーターで指定される型。

### <a name="return-value"></a>戻り値

 `T` 型のオブジェクトへのハンドルのアドレス。

### <a name="remarks"></a>Remarks

この操作は、`T` 型のオブジェクト (存在する場合) の現在の表現を解放し、Agile オブジェクトのデータ メンバーを再初期化し、現在のスレッドのコンテキストを取得し、非アジャイル オブジェクトを表現できるオブジェクトへのハンドル変数のアドレスを返します。 Agile クラス インスタンス オブジェクトを表すためには、代入演算子を使用して、([agile::operator =](#operator-assign)) に、アジャイル クラスのインスタンスにオブジェクトを割り当てます。

## <a name="getaddressofforinout"></a>  Agile::getaddressofforinout メソッド

現在の Agile オブジェクトによって表されるオブジェクトへのハンドルのアドレスを返します。

## <a name="syntax"></a>構文

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型名パラメーターで指定される型。

### <a name="return-value"></a>戻り値

現在の Agile オブジェクトによって表されるオブジェクトへのハンドルのアドレス。

### <a name="remarks"></a>Remarks

この操作は、現在のスレッドのコンテキストを取得し、基になるオブジェクトへのハンドルのアドレスを返します。

## <a name="release"></a>  Agile::release メソッド

現在の Agile オブジェクトの基になるオブジェクトとコンテキストを破棄します。

## <a name="syntax"></a>構文

```cpp
void Release() throw();
```

### <a name="remarks"></a>Remarks

現在の Agile オブジェクトの基になるオブジェクトとコンテキスト (存在する場合) が破棄され、Agile オブジェクトの値が null に設定されます。

## <a name="operator-arrow"></a>  Agile::operator-&gt;演算子

現在の Agile オブジェクトによって表されるオブジェクトへのハンドルを取得します。

## <a name="syntax"></a>構文

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>戻り値

現在の Agile オブジェクトによって表されるオブジェクトへのハンドル。

この演算子は、実際には、非公開の内部型を返します。 戻り値を保持する便利な方法で宣言された変数に割り当てるには、**自動**推論キーワードを入力します。

## <a name="operator-assign"></a>  Agile::operator = 演算子

指定されたオブジェクトを現在のアジャイル オブジェクトに割り当てます。

## <a name="syntax"></a>構文

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型名で指定される型。

*object*<br/>
現在のアジャイル オブジェクトにコピーまたは移動されるオブジェクト、またはオブジェクトへのハンドル。

*lp*<br/>
オブジェクトの IUnknown インターフェイス ポインター。

### <a name="return-value"></a>戻り値

 `T` 型のオブジェクトへのハンドル。

### <a name="remarks"></a>Remarks

代入演算子の 1 つ目のバージョンは、参照型へのハンドルを現在のアジャイル オブジェクトにコピーします。 2 つ目のバージョンは、アジャイル型への参照を現在のアジャイル オブジェクトにコピーします。 3 つ目のバージョンは、アジャイル型を現在のアジャイル オブジェクトに移動します。 4 つ目のバージョンは、COM オブジェクトへのポインターを現在のアジャイル オブジェクトに移動します。

代入演算は、現在のアジャイル オブジェクトのコンテキストを自動的に保持します。

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](platform-namespace-c-cx.md)
