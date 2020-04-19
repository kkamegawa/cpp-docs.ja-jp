---
title: Platform::Exception クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: d37d55c56e3c23d8d9129c985cb4272d2e3ee47a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368735"
---
# <a name="platformexception-class"></a>Platform::Exception クラス

アプリケーションの実行中に発生したエラーを表します。 カスタム例外クラスは、 `Platform::Exception`から派生できません。 カスタム例外が必要な場合は、 `Platform::COMException` を使用し、アプリケーション特有の HRESULT を指定できます。

## <a name="syntax"></a>構文

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>メンバー

`Exception` クラスは、 `Object` クラス、および `IException`、 `IPrintable`、および `IEquatable` の各インターフェイスから継承します。

`Exception` クラスには、次の種類のメンバーもあります。

### <a name="constructors"></a>コンストラクター

|メンバー|説明|
|------------|-----------------|
|[Exception::Exception](#ctor)|`Exception` クラスの新しいインスタンスを初期化します。|

### <a name="methods"></a>メソッド

`Exception`クラスの継承、 `Equals()`、 `Finalize()`、`GetHashCode()`、`GetType()`、`MemberwiseClose()`、および`ToString()`からメソッド、 [platform::object Class](../cppcx/platform-object-class.md)します。 `Exception` クラスには、次のメソッドもあります。

|メンバー|説明|
|------------|-----------------|
|[Exception::CreateException](#createexception)|指定された HRESULT 値を表す例外を作成します。|

### <a name="properties"></a>プロパティ

Exception クラスには、次のプロパティもあります。

|メンバー|説明|
|------------|-----------------|
|[Exception::HResult](#hresult)|例外に対応する HRESULT。|
|[Exception::Message](#message)|例外について説明するメッセージ。 この値は読み取り専用で、 `Exception` が構築された後は変更できません。|

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd

## <a name="createexception"></a> Exception::createexception メソッド

指定した HRESULT 値から Platform::Exception^ を作成します。

### <a name="syntax"></a>構文

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>パラメーター

*hr*<br/>
通常は COM メソッドを呼び出すことによって取得した HRESULT 値。 このメソッドがスローする場合は、値は 0 で、S_OK と等しい場合は、 [platform::invalidargumentexception](../cppcx/platform-invalidargumentexception-class.md)のため、成功する COM メソッドが例外をスローする必要があります。

*message*<br/>
エラーを説明する文字列。

### <a name="return-value"></a>戻り値

エラー HRESULT を表す例外。

### <a name="remarks"></a>Remarks

COM インターフェイスのメソッドに対する呼び出しなどから、返された HRESULT から例外を作成するには、このメソッドを使用します。 カスタム メッセージを表示するために、String^ パラメーターを受け取るオーバーロードを使用することもできます。

厳密に厳密に型指定された例外を作成する CreateException を使用する推奨ではなく作成が、 [platform::comexception](../cppcx/platform-comexception-class.md)だけで、HRESULT を格納しています。

## <a name="ctor"></a>  Exception::exception コンス トラクター

Exception クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>パラメーター

*hresult*<br/>
例外で表されるエラー HRESULT。

*message*<br/>
例外に関連付けられているユーザー指定のメッセージ (規範的テキストなど)。 一般に、エラーが発生した方法と理由についてできるだけ具体的に説明するメッセージを提供する、2 番目のオーバーロードを優先する必要があります。

## <a name="hresult"></a>  Exception::hresult プロパティ

例外に対応する HRESULT。

### <a name="syntax"></a>構文

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>プロパティ値

HRESULT 値。

### <a name="remarks"></a>Remarks

ほとんどの例外は、HRESULT 値の形で返される COM エラーとして開始されます。 C++/CX はこれらの値を Platform::Exception^ オブジェクトに変換し、このプロパティは元のエラー コードの値を格納します。

## <a name="message"></a> Exception::message プロパティ

エラーを説明するメッセージです。

### <a name="syntax"></a>構文

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>プロパティ値

Windows ランタイムで発生する例外では、システムで用意されているエラーの説明になります。

### <a name="remarks"></a>Remarks

Windows 8 で、このプロパティは読み取り専用ため、そのバージョンの Windows ランタイムで例外が HRESULT として ABI 間で転送されます。 Windows 8.1 では、豊富な例外情報が ABI 経由で伝達され、開発者はカスタム メッセージを提供し、他のコンポーネントにはプログラムでそのメッセージにアクセスすることができます。 詳細については、次を参照してください。[例外 (C++/CX)](../cppcx/exceptions-c-cx.md)します。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
