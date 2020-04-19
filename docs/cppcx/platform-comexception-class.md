---
title: Platform::COMException クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: eb6f3e0e4860687d0d47294e11b7741294abac20
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500544"
---
# <a name="platformcomexception-class"></a>Platform::COMException クラス

アプリケーションの実行中に発生する COM エラーを表します。 COMException は、一連の定義済みの標準例外の基底クラスです。

## <a name="syntax"></a>構文

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>メンバー

COMException クラスは、Object クラスと IException、IPrintable、および IEquatable インターフェイスから継承されます。

COMException には次の種類のメンバーもあります。

**コンストラクター**

|メンバー|説明|
|------------|-----------------|
|[COMException](#ctor)|COMException クラスの新しいインスタンスを初期化します。|

**メソッド**

COMException クラスは、 [Platform::Object Class](../cppcx/platform-object-class.md)から Equals()、Finalize()、GetHashCode()、GetType()、MemberwiseClose()、および ToString() メソッドを継承します。

**Properties**

COMException クラスには、次のプロパティがあります。

|メンバー|説明|
|------------|-----------------|
|[Exception::HResult](#hresult)|例外に対応する HRESULT。|
|[Exception::Message](#message)|例外を説明するメッセージ。|

## <a name="derived-exceptions"></a>派生例外

次の定義済みの例外は COMException から派生します。 これらは、その名前、コンストラクターの名前、および基になる HRESULT 値だけが COMException とは異なります。

|名前|基になる HRESULT|説明|
|----------|------------------------|-----------------|
|COMException|*ユーザー定義の hresult*|COM メソッドの呼び出しから認識されない HRESULT が返されるとスローされます。|
|AccessDeniedException|E_ACCESSDENIED|リソースや機能へのアクセスが拒否されるとスローされます。|
|ChangedStateException|E_CHANGED_STATE|親コレクションが変更された後にコレクション反復子またはコレクション ビューのメソッドが呼び出されるとスローされ、メソッドの結果を無効にします。|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|COM クラスが登録されていないときにスローされます。|
|DisconnectedException|RPC_E_DISCONNECTED|オブジェクトがクライアントから接続を切断されるとスローされます。|
|FailureException|E_FAIL|操作が失敗したときにスローされます。|
|InvalidArgumentException|E_INVALIDARG|メソッドに渡された引数のいずれかが無効な場合にスローされます。|
|InvalidCastException|E_NOINTERFACE|型が別の型にキャストできないときにスローされます。|
|NotImplementedException|E_NOTIMPL|インターフェイス メソッドがクラスに実装されていないときにスローされます。|
|NullReferenceException|E_POINTER|null オブジェクト参照を逆参照しようするとスローされます。|
|OperationCanceledException|E_ABORT|操作が中止されるとスローされます。|
|OutOfBoundsException|E_BOUNDS|操作が有効範囲外のデータにアクセスを試みるとスローされます。|
|OutOfMemoryException|E_OUTOFMEMORY|メモリが不足して操作を完了できないときにスローされます。|

### <a name="requirements"></a>必要条件

**サポートされている最低限のクライアント:** Windows 8

**サポートされる最小サーバー:** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd

## <a name="ctor"></a>COMException:: COMException コンストラクター

COMException クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>パラメーター

*hresult*<br/>
例外で表されるエラー HRESULT。

## <a name="hresult"></a>COMException:: HResult プロパティ

例外に対応する HRESULT。

### <a name="syntax"></a>構文

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>プロパティ値

エラーを指定する HRESULT 値。

### <a name="remarks"></a>Remarks

HRESULT 値を解釈する方法の詳細については、「 [COM エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。

## <a name="message"></a>COMException:: Message プロパティ

例外を説明するメッセージ。

### <a name="syntax"></a>構文

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>プロパティ値

例外の説明。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
