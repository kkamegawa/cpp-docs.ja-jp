---
title: '方法: アクティブ化し、WRL を使用した Windows ランタイム コンポーネントを使用します。'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 4b8ce40e6c28f952596cab48848873be91b73c95
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336517"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>方法: アクティブ化し、WRL を使用した Windows ランタイム コンポーネントを使用します。

このドキュメントでは、Windows ランタイム C++ テンプレート ライブラリ (WRL) を使用して、Windows ランタイムを初期化する方法とアクティブ化し、Windows ランタイム コンポーネントを使用する方法を示します。

コンポーネントを使用するには、コンポーネントによって実装されている型へのインターフェイス ポインターを取得する必要があります。 Windows ランタイムの基になるテクノロジは、コンポーネント オブジェクト モデル (COM) であるため、型のインスタンスを維持するために COM 規則に従ってください必要があります。 たとえば、維持する必要があります、*参照カウントを*型がメモリから削除されたときを決定します。

Windows ランタイム C++ テンプレート ライブラリを Windows ランタイムの使用を簡素化するには、スマート ポインター テンプレートを提供します[ComPtr\<T >](comptr-class.md)、参照カウントを自動的に実行します。 変数を宣言するときに指定`ComPtr<`*インターフェイス名*`>` *識別子*します。 インターフェイスのメンバーにアクセスするには、識別子に矢印のメンバー アクセス演算子 (`->`) を適用します。

> [!IMPORTANT]
> インターフェイスの関数を呼び出すときに常に HRESULT 戻り値をテストします。

## <a name="activating-and-using-a-windows-runtime-component"></a>Windows ランタイム コンポーネントのアクティブ化と使用

使用して、次の手順、`Windows::Foundation::IUriRuntimeClass`アクティベーション ファクトリを Windows ランタイム コンポーネントの作成し、そのコンポーネントのインスタンスを作成、プロパティの値を取得する方法を示すインターフェイスです。 また、Windows ランタイムを初期化する方法を示します。 完全な例を次に示します。

> [!IMPORTANT]
> 通常は、ユニバーサル Windows プラットフォーム (UWP) アプリで Windows ランタイム C++ テンプレート ライブラリを使用して、この例は、図のコンソール アプリを使用します。 などの関数`wprintf_s`UWP アプリからは使用できません。 型および UWP アプリで使用できる関数の詳細については、次を参照してください。[ユニバーサル Windows プラットフォーム アプリでサポートされない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)と[Win32 および COM UWP アプリの](/uwp/win32-and-com/win32-and-com-for-uwp-apps)します。

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Windows ランタイム コンポーネントをアクティブ化して使用するには

1. 含まれます (`#include`) 必須の Windows ランタイム、Windows ランタイム C++ テンプレート ライブラリ、または C++ 標準ライブラリ ヘッダー。

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   コードを読みやすくするために、.cpp ファイルでは `using namespace` ディレクティブを使用することをお勧めします。

2. アプリが実行されるスレッドを初期化します。 すべてのアプリケーションでスレッドとスレッド モデルを初期化する必要があります。 この例では、 [Microsoft::WRL::Wrappers::RoInitializeWrapper](roinitializewrapper-class.md) Windows ランタイムを初期化するためにクラスを指定します[RO_INIT_MULTITHREADED](https://msdn.microsoft.com/library/windows/apps/br224661.aspx)スレッド モデルとして。 `RoInitializeWrapper` クラスでは、構築時に `Windows::Foundation::Initialize` を呼び出し、破棄時に `Windows::Foundation::Uninitialize` を呼び出します。

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   2 番目のステートメントで、 [RoInitializeWrapper::HRESULT](roinitializewrapper-class.md#hresult)演算子を返します、`HRESULT`への呼び出しから`Windows::Foundation::Initialize`します。

3. 作成、*アクティベーション ファクトリ*の`ABI::Windows::Foundation::IUriRuntimeClassFactory`インターフェイス。

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Windows ランタイム型を識別するために完全修飾名を使用します。 `RuntimeClass_Windows_Foundation_Uri`パラメーターは、文字列は、Windows ランタイムによって提供され、必要なランタイム クラス名を含むです。

4. 初期化を[Microsoft::WRL::Wrappers::HString](hstring-class.md) URI を表す変数`"http://www.microsoft.com"`します。

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   Windows ランタイムで、Windows ランタイムを使用する文字列のメモリは割り当てません。 代わりに、Windows ランタイムでは、ことを保持し、操作を使用し、作成されたことをバッファーへのハンドルを返します、バッファーに文字列のコピーを作成します。

5. `IUriRuntimeClassFactory::CreateUri` ファクトリ メソッドを使用して、`ABI::Windows::Foundation::IUriRuntimeClass` オブジェクトを作成します。

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. `IUriRuntimeClass::get_Domain` メソッドを呼び出し、`Domain` プロパティの値を取得します。

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. ドメイン名をコンソールに出力して返ります。 すべての `ComPtr` オブジェクトと RAII オブジェクトは自動的にスコープから外れて解放されます。

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](https://msdn.microsoft.com/library/windows/apps/br224636.aspx)関数は、URI 文字列の基になる Unicode 形式を取得します。

完全な例を次に示します。

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするにコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付ける`wrl-consume-component.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)