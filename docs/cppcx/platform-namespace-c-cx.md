---
title: プラットフォーム名前空間 (C++/CX)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform/Platform
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
ms.openlocfilehash: ffbfdde1a9c610f6bcb2356a26acb2b85ed9624a
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345770"
---
# <a name="platform-namespace-ccx"></a>プラットフォーム名前空間 (C++/CX)

Windows ランタイムと互換性のある組み込み型を格納します。

## <a name="syntax"></a>構文

```cpp
using namespace Platform;
```

### <a name="members"></a>メンバー

**属性**

Platform 名前空間は、属性、クラス、列挙体、インターフェイス、および構造体を格納します。 Platform には、入れ子になった名前空間も含まれます。

|属性|説明|
|---------------|-----------------|
|フラグ|列挙体をビット フィールド、つまりフラグのセットとして扱えることを示します。|
|MTAThread|アプリケーションのスレッド モデルがマルチスレッド アパートメント (MTA) であることを示します。|
|STAThread|アプリケーションのスレッド モデルがシングル スレッド アパートメント (STA) であることを示します。|

**クラス**

Platform 名前空間には、次のクラスがあります。

|クラス|説明|
|-----------|-----------------|
|[Platform::AccessDeniedException クラス](../cppcx/platform-accessdeniedexception-class.md)|リソースまたは機能へのアクセスが拒否されたときに発生します。|
|[Platform::Agile クラス](../cppcx/platform-agile-class.md)|非アジャイル オブジェクトを、アジャイル オブジェクトとして表します。|
|[Platform::Array クラス](../cppcx/platform-array-class.md)|変更可能な 1 次元配列を表します。|
|[Platform::ArrayReference クラス](../cppcx/platform-arrayreference-class.md)|コピー操作を最小限にとどめるために初期化が最適化されている配列を表します。|
|[Platform::Box クラス](../cppcx/platform-box-class.md)|Windows::Foundation::DateTime や int64 などの値型がアプリケーション バイナリ インターフェイス (ABI) を越えて渡されるか、型 [Platform::Object^](../cppcx/platform-object-class.md)の変数に格納されるときに、その型をカプセル化するボックス化された型を宣言するために使用します。|
|[Platform::ChangedStateException クラス](../cppcx/platform-changedstateexception-class.md)|親コレクションが変更された後にコレクション反復子またはコレクション ビューのメソッドが呼び出されるとスローされ、メソッドの結果を無効にします。|
|[Platform::ClassNotRegisteredException クラス](../cppcx/platform-classnotregisteredexception-class.md)|COM クラスが登録されていないときにスローされます。|
|[Platform::COMException クラス](../cppcx/platform-comexception-class.md)|認識されない値が COM メソッドの呼び出しから返されたときにスローされる例外を表します。|
|[Platform::Delegate クラス](../cppcx/platform-delegate-class.md)|コールバック関数のシグニチャを表します。|
|[Platform::DisconnectedException クラス](../cppcx/platform-disconnectedexception-class.md)|オブジェクトが、クライアントへの接続を切断しました。|
|[Platform::Exception クラス](../cppcx/platform-exception-class.md)|アプリケーションの実行中に発生したエラーを表します。 例外の基底クラス。|
|[Platform::FailureException クラス](../cppcx/platform-failureexception-class.md)|操作が失敗したときにスローされます。 これは E_FAIL HRESULT と同等です。|
|[Platform::Guid 値クラス](../cppcx/platform-guid-value-class.md)|Windows ランタイムの型システムで GUID を表します。|
|[Platform::InvalidArgumentException クラス](../cppcx/platform-invalidargumentexception-class.md)|メソッドに渡された引数のいずれかが無効な場合にスローされます。|
|[Platform::InvalidCastException クラス](../cppcx/platform-invalidcastexception-class.md)|無効なキャストまたは明示的な変換が発生したときにスローされます。|
|[Platform::MTAThreadAttribute クラス](../cppcx/platform-mtathreadattribute-class.md)|アプリケーションのスレッド モデルがマルチスレッド アパートメント (MTA) であることを示します。|
|[Platform::NotImplementedException クラス](../cppcx/platform-notimplementedexception-class.md)|インターフェイス メソッドがクラスに実装されていないときにスローされます。|
|[Platform::NullReferenceException クラス](../cppcx/platform-nullreferenceexception-class.md)|null オブジェクト参照を逆参照しようするとスローされます。|
|[Platform::Object クラス](../cppcx/platform-object-class.md)|共通の動作を提供する基底クラス。|
|[Platform::ObjectDisposedException クラス](../cppcx/platform-objectdisposedexception-class.md)|破棄されたオブジェクトで操作が実行されるとスローされます。|
|[Platform::OperationCanceledException クラス](../cppcx/platform-operationcanceledexception-class.md)|操作が中止されるとスローされます。|
|[Platform::OutOfBoundsException クラス](../cppcx/platform-outofboundsexception-class.md)|操作が有効範囲外のデータにアクセスを試みるとスローされます。|
|[Platform::OutOfMemoryException クラス](../cppcx/platform-outofmemoryexception-class.md)|メモリが不足して操作を完了できないときにスローされます。|
|[Platform::STAThreadAttribute クラス](../cppcx/platform-stathreadattribute-class.md)|アプリケーションのスレッド モデルがシングル スレッド アパートメント (STA) であることを示します。|
|[Platform::String クラス](../cppcx/platform-string-class.md)|テキストを表現するために使用される Unicode 文字のシーケンシャル コレクション。|
|[Platform::StringReference クラス](../cppcx/platform-stringreference-class.md)|コピーのオーバーヘッドを最小限に抑えて、文字列バッファーにアクセスできます。|
|[Platform::Type クラス](../cppcx/platform-type-class.md)|組み込み型をカテゴリ列挙体ごとに識別します。|
|[Platform::ValueType クラス](../cppcx/platform-valuetype-class.md)|値の型のインスタンスの基底クラス。|
|[Platform::WeakReference クラス](../cppcx/platform-weakreference-class.md)|参照カウントをインクリメントしない、ref クラス オブジェクトへの弱い参照を提供します。|
|[Platform::WriteOnlyArray クラス](../cppcx/platform-writeonlyarray-class.md)|FillArray パターンを実装するメソッドの入力パラメーターとして使用される書き込み専用の 1 次元配列を表します。|
|[Platform::WrongThreadException クラス](../cppcx/platform-wrongthreadexception-class.md)|スレッドが、スレッドのアパートメントに属さないプロキシ オブジェクト用のインターフェイス ポインターを通じて呼び出すときにスローされます。|

**インターフェイスの実装**

Platform 名前空間は、次のインターフェイスを定義します。

|Interface|説明|
|---------------|-----------------|
|[Platform::IBox インターフェイス](../cppcx/platform-ibox-interface.md)|パラメーターが Platform::Object^ として入力された関数に値型を渡すために使用します。|
|[Platform::IBoxArray インターフェイス](../cppcx/platform-iboxarray-interface.md)|パラメーターが Platform::Array として入力された関数に値型の配列を渡すために使用されるインターフェイス。|
|[Platform::IDisposable インターフェイス](../cppcx/platform-idisposable-interface.md)|アンマネージ リソースを解放するために使用されます。|

**列挙体**

Platform 名前空間には、次の列挙体があります。

|Interface|説明|
|---------------|-----------------|
|[Platform::CallbackContext 列挙型](../cppcx/platform-callbackcontext-enumeration.md)|デリゲート コンストラクターのパラメーターとして使用される列挙体。 コールバックを、元のスレッドにマーシャリングするか、呼び出し元のスレッドにマーシャリングするかを判定します。|
|[Platform::TypeCode 列挙型](../cppcx/platform-typecode-enumeration.md)|組み込み型を表す数値カテゴリを指定します。|

**構造体**

Platform 名前空間には、次の構造体があります。

|構造体|説明|
|---------------|-----------------|
|[Platform::Enum クラス](../cppcx/platform-enum-class.md)|名前付き定数を表します。|
|[Platform::Guid 値クラス](../cppcx/platform-guid-value-class.md)|GUID を表します。|
|[Platform::IntPtr 値クラス](../cppcx/platform-intptr-value-class.md)|サイズがプラットフォームに適した (32 ビットまたは 64 ビット) 符号付きポインター。|
|[Platform::SizeT 値クラス](../cppcx/platform-sizet-value-class.md)|オブジェクトのサイズを表すために使用される符号なしのデータ型。|
|[Platform::UIntPtr 値クラス](../cppcx/platform-uintptr-value-class.md)|サイズがプラットフォームに適した (32 ビットまたは 64 ビット) 符号なしポインター。|

## <a name="see-also"></a>関連項目

[Platform::Collections 名前空間](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Runtime::CompilerServices 名前空間](../cppcx/platform-runtime-compilerservices-namespace.md)<br/>
[Platform::Runtime::InteropServices 名前空間](../cppcx/platform-runtime-interopservices-namespace.md)<br/>
[Platform::Metadata 名前空間](../cppcx/platform-metadata-namespace.md)
