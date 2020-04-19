---
title: 'チュートリアル: WRL および Media Foundation を使用した UWP アプリの作成'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: ac2c16fb94646af7445d41010253967be126636a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498304"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>チュートリアル: WRL および Media Foundation を使用した UWP アプリの作成

> [!NOTE]
> 新しい UWP アプリとコンポーネントは、お勧めしますを使用すること[C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)、新しい標準 c++ 17 の言語プロジェクションの Windows ランタイム Api です。 C++/WinRT はバージョン 1803 以降から Windows 10 SDK で使用できます。 C++/WinRT はヘッダー ファイル、完全に実装されは最新の Windows API にファースト クラスのアクセス提供するために設計されています。

このチュートリアルでは、Windows ランタイムC++テンプレートライブラリ (wrl) を使用して、 [Microsoft メディアファンデーション](/windows/win32/medfound/microsoft-media-foundation-sdk)を使用するユニバーサル Windows プラットフォーム (UWP) アプリを作成する方法について説明します。

この例では、Web カメラからキャプチャしたイメージにグレースケール効果を適用するカスタム メディア ファンデーション変換を作成します。 アプリでは、カスタム変換の定義のために C++ を使用し、キャプチャしたイメージを変換するコンポーネントを使用するために C# を使用しています。

> [!NOTE]
> C# の代わりに、JavaScript、Visual Basic、または C++ でカスタム変換コンポーネントを使用することもできます。

ほとんどの場合、/Cx を使用C++して Windows ランタイムを作成できます。 ただし、場合によっては、WRL を使用する必要があります。 たとえば、Microsoft メディアファンデーション用のメディア拡張機能を作成する場合は、COM インターフェイスと Windows ランタイムインターフェイスの両方を実装するコンポーネントを作成する必要があります。 C++/Cx では Windows ランタイムオブジェクトを作成できるだけなので、メディア拡張機能を作成するには、、COM インターフェイスと Windows ランタイムインターフェイスの両方の実装を有効にするため、wrl を使用する必要があります。

> [!NOTE]
> このコード例は長いですが、役に立つメディア ファンデーション変換を作成するために必要な最低限のコードを示しています。 独自のカスタム変換を作成するための出発点として、このコード例を使用することができます。 この例は、メディア拡張機能の[サンプル](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)で、メディア拡張機能を使用してビデオに効果を適用し、ビデオをデコードし、メディアストリームを生成するスキームハンドラーを作成しています。

## <a name="prerequisites"></a>必須コンポーネント

- Visual Studio 2017 以降では、UWP サポートはオプションのコンポーネントです。 インストールするには、Windows の [スタート] メニューから Visual Studio インストーラーを開き、使用している Visual Studio のバージョンを確認します。 **[変更]** を選択し、 **[ユニバーサル Windows プラットフォームの開発]** タイルがオンになっていることを確認します。 **[オプションのコンポーネント]** で、visual studio 2017 の **C++ uwp (v141) のツール**、または **C++ visual studio 2019 用の tools for uwp (v142)** を確認します。 次に、使用する Windows SDK のバージョンを確認します。 

- [Windows ランタイム](/uwp/api/)の使用経験があります。

- COM の使用経験。

- Web カメラ。

## <a name="key-points"></a>主要なポイント

- カスタム メディア ファンデーション コンポーネントを作成するには、Microsoft インターフェイス定義言語 (MIDL) の定義ファイルを使用してインターフェイスを定義し、そのインターフェイスを実装して、他のコンポーネントからアクティブ化できるようにします。

- 属性と属性`NTDDI_WIN8`、および[バージョン](/windows/win32/Midl/version)属性値は、wrl を使用するメディアファンデーションコンポーネントの MIDL 定義の重要な部分です。`namespace` `runtimeclass`

- [Microsoft:: WRL:: RuntimeClass](runtimeclass-class.md)は、カスタムメディアファンデーションコンポーネントの基本クラスです。 テンプレート引数として指定されている[Microsoft:: WRL:: RuntimeClassType:: WinRtClassicComMix](runtimeclasstype-enumeration.md)列挙値は、クラスを Windows ランタイムクラスとして、また従来の COM ランタイムクラスとして使用するようにマークします。

- [InspectableClass](inspectableclass-macro.md)マクロは、参照カウントや`QueryInterface`メソッドなどの基本的な COM 機能を実装し、ランタイムクラス名と信頼レベルを設定します。

- Microsoft:: WRL::[Module クラス](module-class.md)を使用して、 [DllGetActivationFactory](/windows/win32/winrt/functions)、 [DLLCANUNLOADNOW](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)、 [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)などの DLL エントリポイント関数を実装します。

- コンポーネント DLL を runtimeobject.lib にリンクします。 また、Windows メタデータを生成するには、リンカー行に[/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md)を指定します。

- プロジェクト参照を使用して、WRL コンポーネントに UWP アプリからアクセスできるようにします。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>WRL を使用してメディアファンデーショングレースケール変換コンポーネントを作成するには

1. Visual Studio で、空の**ソリューション**プロジェクトを作成します。 プロジェクトに*MediaCapture*のように名前を指定します。

1. **DLL (ユニバーサル Windows)** プロジェクトをソリューションに追加します。 プロジェクトに「*グレースケール変換*」などの名前を指定します。

1. **Midl ファイル (.idl)** ファイルをプロジェクトに追加します。 ファイルに「*グレースケール変換*」などの名前を指定します。

1. 次のコードを、「グレースケール変換」に追加します。

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 次のコードを使用して、の`pch.h`内容を置き換えます。

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. 新しいヘッダーファイルをプロジェクトに追加し、という`BufferLock.h`名前を付けて、内容を次のコードに置き換えます。

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`この例では、は使用されません。 このファイルは必要に応じてプロジェクトから削除できます。

1. 次のコードを使用して、の`GrayscaleTransform.cpp`内容を置き換えます。

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. 新しいモジュール定義ファイルをプロジェクトに追加し、という`GrayscaleTransform.def`名前を指定して、次のコードを追加します。

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 次のコードを使用して、の`dllmain.cpp`内容を置き換えます。

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. プロジェクトの **[プロパティページ]** ダイアログボックスで、次の**リンカー**プロパティを設定します。

   1. **[入力]** の **[モジュール定義ファイル]** で`GrayScaleTransform.def`、を指定します。

   1. また、 **[入力]** `runtimeobject.lib`で、、 `mfplat.lib` 、およびを **[追加の依存関係]** プロパティに追加`mfuuid.lib`します。

   1. **Windows メタデータ** 設定 **Windows メタデータの生成** に **[はい] (/WINMD)** します。

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>C#アプリからカスタムメディアファンデーションコンポーネントの wrl を使用するには

1. 新しい **C#空のアプリ (ユニバーサル Windows)** `MediaCapture`プロジェクトをソリューションに追加します。 プロジェクトに*MediaCapture*のように名前を指定します。

1. **MediaCapture**プロジェクトで、 `GrayscaleTransform`プロジェクトへの参照を追加します。 詳細については[、「方法:参照マネージャーを使用して参照を追加または削除する](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)

1. の [機能] タブで、[**マイク**と**web カメラ**] を選択します。 `Package.appxmanifest` Web カメラから写真をキャプチャするために、両方の機能が必要です。

1. で`MainPage.xaml`、次のコードをルートの[Grid](/uwp/api/Windows.UI.Xaml.Controls.Grid)要素に追加します。

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 次のコードを使用して、の`MainPage.xaml.cs`内容を置き換えます。

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

を`MediaCapture app`次の図に示します。

![MediaCapture アプリで写真をキャプチャする](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>次の手順

例では、既定の Web カメラから写真を 1 枚ずつキャプチャする方法を示します。 [メディア拡張機能のサンプル](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)ではさらに多くのことができます。 そのサンプルでは、Web カメラ デバイスを列挙し、ローカル スキーム ハンドラーを使用する方法や、個別の写真とビデオ ストリームの両方で機能する追加のメディア効果について示します。

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft メディア ファンデーション](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[メディア拡張機能のサンプル](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
