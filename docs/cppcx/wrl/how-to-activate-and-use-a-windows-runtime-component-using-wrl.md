---
title: '方法: WRL を使用して Windows ランタイムコンポーネントをアクティブ化して使用する'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 59a031968933ab151dc97a8089aff629026f5ea5
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926061"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>方法: WRL を使用して Windows ランタイムコンポーネントをアクティブ化して使用する

このドキュメントでは、Windows ランタイムC++テンプレートライブラリ (wrl) を使用して Windows ランタイムを初期化する方法と、Windows ランタイムコンポーネントをアクティブ化して使用する方法について説明します。

コンポーネントを使用するには、コンポーネントによって実装されている型へのインターフェイス ポインターを取得する必要があります。 また、Windows ランタイムの基になるテクノロジはコンポーネントオブジェクトモデル (COM) であるため、型のインスタンスを維持するには、COM の規則に従う必要があります。 たとえば、型がいつメモリから削除されるかを決定する*参照カウント*を維持する必要があります。

Windows ランタイムの使用を簡単にするためにC++ 、Windows ランタイムテンプレートライブラリには、参照カウントを自動的に実行するスマートポインターテンプレート[comptr\<T >](comptr-class.md)が用意されています。 変数を宣言するときは、 `ComPtr<`*インターフェイス名*`>`の*識別子*を指定します。 インターフェイスのメンバーにアクセスするには、識別子に矢印のメンバー アクセス演算子 (`->`) を適用します。

> [!IMPORTANT]
> インターフェイス関数を呼び出す場合は、常に HRESULT の戻り値をテストします。

## <a name="activating-and-using-a-windows-runtime-component"></a>Windows ランタイム コンポーネントのアクティブ化と使用

次の手順では`Windows::Foundation::IUriRuntimeClass` 、インターフェイスを使用して、Windows ランタイムコンポーネントのアクティベーションファクトリを作成し、そのコンポーネントのインスタンスを作成して、プロパティ値を取得する方法を示します。 また、Windows ランタイムを初期化する方法についても説明します。 完全な例を次に示します。

> [!IMPORTANT]
> 通常は、ユニバーサル Windows プラットフォーム (UWP C++ ) アプリで Windows ランタイムテンプレートライブラリを使用しますが、この例ではコンソールアプリを使用して説明します。 などの関数は、UWP アプリからは使用できません。 `wprintf_s` UWP アプリで使用できる型と関数の詳細については、「[ユニバーサル Windows プラットフォームアプリでサポートされない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」および「 [Uwp アプリの Win32 および COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)」を参照してください。

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Windows ランタイム コンポーネントをアクティブ化して使用するには

1. 必須の Windows ランタイム、Windows ランタイムC++テンプレートライブラリ、またはC++標準ライブラリヘッダーを含めます。`#include`

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   コードを読みやすくするために、.cpp ファイルでは `using namespace` ディレクティブを使用することをお勧めします。

2. アプリが実行されるスレッドを初期化します。 すべてのアプリケーションでスレッドとスレッド モデルを初期化する必要があります。 この例では、 [Microsoft:: WRL:: wrapper:: RoInitializeWrapper](roinitializewrapper-class.md)クラスを使用して Windows ランタイムを初期化し、 [RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type)をスレッドモデルとして指定します。 `RoInitializeWrapper` クラスでは、構築時に `Windows::Foundation::Initialize` を呼び出し、破棄時に `Windows::Foundation::Uninitialize` を呼び出します。

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   2番目のステートメントでは、 [roinitializewrapper:: HRESULT](roinitializewrapper-class.md#hresult)演算子`HRESULT`は、の呼び出し`Windows::Foundation::Initialize`からを返します。

3. `ABI::Windows::Foundation::IUriRuntimeClassFactory`インターフェイスの*アクティベーションファクトリ*を作成します。

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Windows ランタイムは、完全修飾名を使用して型を識別します。 `RuntimeClass_Windows_Foundation_Uri`パラメーターは、Windows ランタイムによって提供される文字列であり、必要なランタイムクラス名が含まれています。

4. URI`"https://www.microsoft.com"`を表す[Microsoft:: Wrl:: Wrapper:: hstring](hstring-class.md)変数を初期化します。

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   Windows ランタイムでは、Windows ランタイムが使用する文字列にメモリを割り当てません。 代わりに、Windows ランタイムは、保持して操作に使用するバッファーに文字列のコピーを作成し、作成されたバッファーへのハンドルを返します。

5. `IUriRuntimeClassFactory::CreateUri` ファクトリ メソッドを使用して、`ABI::Windows::Foundation::IUriRuntimeClass` オブジェクトを作成します。

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. `IUriRuntimeClass::get_Domain` メソッドを呼び出し、`Domain` プロパティの値を取得します。

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. ドメイン名をコンソールに出力して返ります。 すべての `ComPtr` オブジェクトと RAII オブジェクトは自動的にスコープから外れて解放されます。

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)関数は、基になる Unicode 形式の URI 文字列を取得します。

完全な例を次に示します。

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするには、コードをコピーし、visual studio プロジェクトに貼り付けるか、という名前`wrl-consume-component.cpp`のファイルに貼り付けてから、visual studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)