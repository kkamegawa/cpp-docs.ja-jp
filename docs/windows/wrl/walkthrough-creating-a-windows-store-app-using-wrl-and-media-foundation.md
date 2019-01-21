---
title: 'チュートリアル: WRL および Media Foundation を使用して UWP アプリの作成'
ms.date: 09/17/2018
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: e6d240152c3740b59c34ae8e0f5aa818ce8be638
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337353"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>チュートリアル: WRL および Media Foundation を使用して UWP アプリの作成

Windows ランタイム C++ テンプレート ライブラリ (WRL) を使用して、使用するユニバーサル Windows プラットフォーム (UWP) アプリを作成する方法について説明します[Microsoft メディア ファンデーション](/windows/desktop/medfound/microsoft-media-foundation-sdk)します。

この例では、Web カメラからキャプチャしたイメージにグレースケール効果を適用するカスタム メディア ファンデーション変換を作成します。 アプリでは、カスタム変換の定義のために C++ を使用し、キャプチャしたイメージを変換するコンポーネントを使用するために C# を使用しています。

> [!NOTE]
> C# の代わりに、JavaScript、Visual Basic、または C++ でカスタム変換コンポーネントを使用することもできます。

ほとんどの場合にを使用することが C +/cli/CX を Windows ランタイムを作成します。 ただし、場合によって、WRL を使用する必要があります。 などの Microsoft メディア ファンデーションのメディア拡張機能を作成するときに、COM および Windows ランタイムの両方のインターフェイスを実装するコンポーネントを作成する必要があります。 ため、C + + CX は Windows ランタイム オブジェクトを作成できるのみ、COM および Windows ランタイムの両方のインターフェイスの実装を可能にするため、メディア拡張機能を作成する、WRL を使用する必要があります。

> [!NOTE]
> このコード例は長いですが、役に立つメディア ファンデーション変換を作成するために必要な最低限のコードを示しています。 独自のカスタム変換を作成するための出発点として、このコード例を使用することができます。 この例の出典元は、[メディア拡張機能サンプル](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)ビデオへの適用を使用してメディア拡張機能の効果、ビデオのデコード、メディア ストリームを生成するスキーム ハンドラーを作成します。

## <a name="prerequisites"></a>必須コンポーネント

- 使用したエクスペリエンス、 [Windows ランタイム](https://msdn.microsoft.com/library/windows/apps/br211377.aspx)します。

- COM の使用経験。

- Web カメラ。

## <a name="key-points"></a>主要なポイント

- カスタム メディア ファンデーション コンポーネントを作成するには、Microsoft インターフェイス定義言語 (MIDL) の定義ファイルを使用してインターフェイスを定義し、そのインターフェイスを実装して、他のコンポーネントからアクティブ化できるようにします。

- `namespace`と`runtimeclass`属性、および`NTDDI_WIN8`[バージョン](/windows/desktop/Midl/version)属性の値は WRL を使用するメディア ファンデーション コンポーネントの MIDL 定義の重要な部分です。

- [:Runtimeclass](runtimeclass-class.md)カスタム メディア ファンデーション コンポーネントの基本クラスです。 [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](runtimeclasstype-enumeration.md)列挙値は、テンプレート引数として提供される、Windows ランタイム クラスとクラシック COM ランタイム クラスの両方に使用するためのクラスをマークします。

- [InspectableClass](inspectableclass-macro.md)マクロは、参照カウントなどの COM 基本機能を実装し、`QueryInterface`メソッド、およびランタイム クラス名と信頼レベルを設定します。

- 使用の microsoft::wrl::[モジュール クラス](module-class.md)など DLL エントリ ポイント関数を実装する[DllGetActivationFactory](https://msdn.microsoft.com/library/br205771.aspx)、 [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow)、および[DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject)します。

- コンポーネント DLL を runtimeobject.lib にリンクします。 指定することも[/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) Windows メタデータを生成するリンカー行にします。

- プロジェクト参照を使用して、WRL コンポーネントを UWP アプリにアクセスできるようにします。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>メディア ファンデーションのグレースケールを作成する WRL 変換コンポーネントを使用するには

1. Visual Studio で、作成、**空のソリューション**プロジェクト。 など、プロジェクトの名前*MediaCapture*します。

1. 追加、 **DLL (ユニバーサル Windows)** プロジェクトがソリューションにします。 など、プロジェクトの名前*GrayscaleTransform*します。

1. 追加、 **Midl ファイル (.idl)** ファイルをプロジェクトにします。 など、ファイルの名前*GrayscaleTransform.idl*します。

1. このコードを GrayscaleTransform.idl に追加します。

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 次のコードを使用して、内容を置き換える`pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. プロジェクトに新しいヘッダー ファイルを追加、名前を付けます`BufferLock.h`、し、内容を次のコードに置き換えます。

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h` この例では使用されません。 このファイルは必要に応じてプロジェクトから削除できます。

1. 次のコードを使用して、内容を置き換える`GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. プロジェクトに新しいモジュール定義ファイルを追加、名前を付けます`GrayscaleTransform.def`、このコードを追加します。

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 次のコードを使用して、内容を置き換える`dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. プロジェクトの**プロパティ ページ** ダイアログ ボックスで、次の設定、**リンカー**プロパティ。

   1. **入力**、用、**モジュール定義ファイル**、指定`GrayScaleTransform.def`します。

   1. また**入力**、追加`runtimeobject.lib`、 `mfuuid.lib`、および`mfplat.lib`を**追加の依存関係**プロパティ。

   1.  **Windows メタデータ**設定**Windows メタデータの生成**に**はい (/WINMD)** します。

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>WRL c# アプリからカスタム メディア ファンデーション コンポーネントを使用するには

1. 新しい追加**c# 空白アプリ (ユニバーサル Windows)** プロジェクトを`MediaCapture`ソリューション。 など、プロジェクトの名前*MediaCapture*します。

1. **MediaCapture**プロジェクトへの参照を追加、`GrayscaleTransform`プロジェクト。 学習する方法についてを参照してください[方法。参照マネージャーを使用して参照を追加または削除する](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)

1. `Package.appxmanifest`の**機能**] タブで [**マイク**と**web カメラ**します。 Web カメラから写真をキャプチャするために、両方の機能が必要です。

1. `MainPage.xaml`、ルートにこのコードを追加[グリッド](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)要素。

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 次のコードを使用して、内容を置き換える`MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

次の図は、`MediaCapture app`します。

![写真をキャプチャする MediaCapture アプリ](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>次の手順

例では、既定の Web カメラから写真を 1 枚ずつキャプチャする方法を示します。 [メディア拡張機能サンプル](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)は以上です。 そのサンプルでは、Web カメラ デバイスを列挙し、ローカル スキーム ハンドラーを使用する方法や、個別の写真とビデオ ストリームの両方で機能する追加のメディア効果について示します。

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk)<br/>
[メディア拡張機能サンプル](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)