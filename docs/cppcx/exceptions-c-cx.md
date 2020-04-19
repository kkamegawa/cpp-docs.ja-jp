---
title: 例外 (C++/CX)
ms.date: 07/02/2019
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: ade406dc5db6022978f83715555c425caef4375b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740178"
---
# <a name="exceptions-ccx"></a>例外 (C++/CX)

/Cx でのC++エラー処理は、例外に基づいています。 最も基本的なレベルでは、Windows ランタイムコンポーネントは、HRESULT 値としてエラーを報告します。 /Cx C++では、これらの値は、HRESULT 値と、プログラムでアクセスできる文字列の説明を含む厳密に型指定された例外に変換されます。  例外は、 `ref class` から派生した `Platform::Exception`として実装されます。  `Platform` 名前空間は、ほとんどの共通 HRESULT 値のために異なる例外クラスを定義します。それ以外のすべての値は、 `Platform::COMException` クラスで報告されます。 すべての例外クラスには、元の HRESULT を取得するために使用できる [Exception::HResult](platform-exception-class.md#hresult) フィールドがあります。 また、例外の元のソースを特定するために、以外C++の言語で記述されたコードで発生した場合でも、呼び出し履歴の情報をデバッガーで調べることができます。

## <a name="exceptions"></a>例外

C++プログラムでは、Windows ランタイム操作、から`std::exception`派生した例外、またはユーザー定義型からの例外をスローしてキャッチできます。 Windows ランタイム例外をスローする必要があるのは、例外をキャッチするコードが JavaScript で記述されている場合など、アプリケーションバイナリインターフェイス (ABI) の境界を越える場合のみです。 非 Windows ランタイムC++例外が ABI 境界に達すると、例外は E_FAIL HRESULT を表す`Platform::FailureException`例外に変換されます。 ABI の詳細については、「 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)」を参照してください。

HRESULT パラメーターを受け取る2つのコンストラクターのいずれかを使用するか、または HRESULT パラメーターと、それを処理する任意の Windows ランタイムアプリに ABI を介して渡すことができる[platform:: String](platform-string-class.md)^ パラメーターを使用して、 [Platform:: Exception](platform-exception-class.md)を宣言できます。 または、1 つの HRESULT パラメーター、または 1 つの HRESULT パラメーターと [パラメーターのいずれかを受け取る 2 つの](platform-exception-class.md#createexception) Exception::CreateException メソッド `Platform::String^` オーバーロードの 1 つを使用して、例外を宣言できます。

## <a name="standard-exceptions"></a>標準の例外

C++/CX は、一般的な HRESULT エラーを表す標準の例外のセットをサポートしています。 この標準例外は [Platform::COMException](platform-comexception-class.md)から派生し、その例外は `Platform::Exception`から派生します。 ABI の境界を越えて例外をスローするときは、標準の例外の 1 つをスローする必要があります。

`Platform::Exception`から独自の例外の種類を派生させることはできません。 カスタム例外をスローするには、ユーザー定義の HRESULT を使用して `COMException` オブジェクトを構築します。

次の表は、標準の例外の一覧を示しています。

|名前|基になる HRESULT|説明|
|----------|------------------------|-----------------|
|COMException|*ユーザー定義の hresult*|COM メソッドの呼び出しから認識されない HRESULT が返されるとスローされます。|
|AccessDeniedException|E\_ACCESSDENIED|リソースや機能へのアクセスが拒否されるとスローされます。|
|ChangedStateException|E\_変更\_された状態|コレクション反復子またはコレクション ビューのメソッドが、親コレクションの変更後に呼び出さたときにスローされます。これにより、メソッドの結果は無効になります。|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|COM クラスが登録されていないときにスローされます。|
|DisconnectedException|RPC\_が切断されまし\_た|オブジェクトがクライアントから接続を切断されるとスローされます。|
|FailureException|E\_失敗|操作が失敗したときにスローされます。|
|InvalidArgumentException|E\_INVALIDARG|メソッドに提供された引数のいずれかが有効でない場合にスローされます。|
|InvalidCastException|E\_NOINTERFACE|型が別の型にキャストできないときにスローされます。|
|NotImplementedException|E\_NOTIMPL|インターフェイス メソッドがクラスに実装されていないときにスローされます。|
|NullReferenceException|E\_ポインター|null オブジェクト参照を逆参照しようするとスローされます。|
|ObjectDisposedException|RO\_E\_終了|破棄されたオブジェクトで操作が実行されるとスローされます。|
|OperationCanceledException|E\_中止|操作が中止されるとスローされます。|
|OutOfBoundsException|E\_境界|操作が有効範囲外のデータにアクセスを試みるとスローされます。|
|OutOfMemoryException|E\_OUTOFMEMORY|メモリが不足して操作を完了できないときにスローされます。|
|WrongThreadException|\_\_RPC に間違ったスレッドがあります\_|スレッドが、スレッドのアパートメントに属さないプロキシ オブジェクト用のインターフェイス ポインターを通じて呼び出すときにスローされます。|

## <a name="hresult-and-message-properties"></a>HResult および Message プロパティ

すべての例外に、 [HResult](platform-comexception-class.md#hresult) プロパティと [Message](platform-comexception-class.md#message) プロパティがあります。 [Exception::HResult](platform-exception-class.md#hresult) プロパティは、例外の基になる数値 HRESULT 値を取得します。 [Exception::Message](platform-exception-class.md#message) プロパティは、例外を記述するシステム指定文字列を取得します。 Windows 8 では、メッセージはデバッガーでのみ使用でき、読み取り専用です。 これは、例外を再スローするときに、例外を変更できないことを意味します。 Windows 8.1 では、例外を再スローする場合に、プログラムでメッセージの文字列にアクセスし、新しいメッセージを提供することができます。 非同期メソッド呼び出しに関する呼び出し履歴を含め、より詳細な呼び出し履歴情報もデバッガーで使用できます。

### <a name="examples"></a>使用例

次の例では、同期操作の Windows ランタイム例外をスローする方法を示します。

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

次の例は、例外をキャッチする方法を示しています。

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

非同期操作中にスローされた例外をキャッチするには、タスククラスを使用して、エラー処理の継続を追加します。 エラー処理コードの継続は、他のスレッドでスローされる例外を呼び出し元のスレッドにマーシャリングして、発生する可能性があるすべての例外をコード中の 1 つのポイントで処理できるようにします。 詳しくは、「 [C++ での非同期プログラミング](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)」を参照してください。

## <a name="unhandlederrordetected-event"></a>UnhandledErrorDetected イベント

Windows 8.1 では、 [Windows:: ApplicationModel:: Core:: CoreApplication:: UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror.unhandlederrordetected)静的イベントをサブスクライブできます。このイベントは、プロセスを停止しようとしている未処理のエラーへのアクセスを提供します。 エラーがどこで発生したかにかかわりなく、イベントの引数によって渡される [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) オブジェクトという形で、このハンドラーに到達します。 オブジェクトに対して `Propagate` を呼び出した場合、エラー コードに対応する型の `Platform::*Exception` が生成され、スローされます。 catch ブロックで、必要に応じて、ユーザー状態を保存することができ、その後、プロセスが `throw`を呼び出して終了すること、またはプログラムを既知の状態に戻すために他の作業を実行することを許可できます。 次の例に、基本的なパターンを示します。

App.xaml の場合:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

App.xaml で、次のようにします。

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
    try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }
}
```

### <a name="remarks"></a>Remarks

C++/Cx は句を`finally`使用しません。

## <a name="see-also"></a>関連項目

[C++/CX 言語リファレンス](visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](namespaces-reference-c-cx.md)
