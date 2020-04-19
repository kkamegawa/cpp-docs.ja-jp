---
title: ユニバーサル Windows プラットフォームへの移植 (C++)
ms.date: 10/23/2019
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
ms.openlocfilehash: 9314cb564e792a7d4949d422a3942e9d46a23cb2
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627200"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>ユニバーサル Windows プラットフォームへの移植 (C++)

このトピックでは、既存の C++ コードを Windows 10 アプリ プラットフォームであるユニバーサル Windows プラットフォームに移植する方法を説明します。 *ユニバーサル*という用語は、Windows 10 を実行する任意のデバイスでコードを実行できることを意味します。 単一のプロジェクトを作成し、Windows 10 を実行している任意のデバイス上で適切に機能する単一の XAML ベースのユーザー インターフェイスも作成します。 XAML で動的なレイアウト機能を使用することで、アプリの UI をさまざまな表示サイズに適合させることができます。

Windows デベロッパー センターのドキュメントには、ユニバーサル Windows プラットフォームへの Windows 8.1 アプリの移植に関するガイドが含まれています。 「[Windows ランタイム 8 から UWP への移行](/windows/uwp/porting/w8x-to-uwp-root)」を参照してください。 ガイドでは主に C# コードに重点を置いていますが、ガイダンスのほとんどが C++ に適用可能です。 以下の手順にはより詳細な情報が記載されています。 「[デスクトップアプリケーションから UWP への移行](/windows/uwp/porting/desktop-to-uwp-migrate)」も参照してください。

このトピックには、UWP へのコードの移植に関する次の手順が含まれています。

- [UWP への Windows 8.1 ストア アプリの移植](#BK_81StoreApp)

- [UWP への Windows 8.1 ランタイム コンポーネントの移植](#BK_81Component)

UWP アプリケーションから従来のデスクトップ Win32 DLL を呼び出したい場合は、それも可能です。 このような手順を使用して、既存の従来 Windows デスクトップ C++ のアプリケーション用に、あるいはクロス プラットフォームの標準 C++ コード用に、UWP ユーザー インターフェイス層を作成することができます。 「[方法: ユニバーサル Windows アプリで既存の C++ コードを使用する](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)」を参照してください。 

## <a name="BK_81StoreApp"></a> UWP への Windows 8.1 ストア アプリの移植

Windows 8.1 ストア アプリがある場合は、この手順を使用して、UWP と Windows 10 を実行しているいずれかのデバイスで動作させることができます。  まず、Visual Studio 2019 を使用してプロジェクトを Windows 8.1 プロジェクトとしてビルドし、コンパイラおよびライブラリの変更に起因する問題を最初に排除することをお勧めします。 それが完了したら、2 種類の方法でこれを Windows 10 UWP プロジェクトに変換することができます。 最も簡単な方法 (次の手順で説明) は、ユニバーサル Windows プロジェクトを作成してから、そこに既存のコードをコピーする方法です。 Windows 8.1 デスクトップと Windows 8.1 Phone でユニバーサル プロジェクトを使用していた場合、プロジェクトは XAML では 2 つの異なるレイアウトで始まりますが、表示サイズに合わせて調整する 1 つの動的レイアウトで終わります。

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>UWP に Windows 8.1 ストア アプリを移植するには

1. まだ実行していない場合は、Visual Studio 2017 で Windows 8.1 アプリ プロジェクトを開き、指示に従ってプロジェクト ファイルをアップグレードします。

   Visual Studio のセットアップで、**Windows 8.1 ツール**をインストールしておく必要があります。 これらのツールがインストールされていない場合は、 **[プログラムと機能]** ウィンドウから **Visual Studio** のセットアップを開始し、 **[Visual Studio 2017]** を選択してから、セットアップ ウィンドウで **[変更]** を選択します。 **Windows 8.1 ツール**を見つけて、それが選択されていることを確認してから **[OK]** をクリックします。

1. **[プロジェクトのプロパティ]** ウィンドウを開き、 **[C++]** の **[全般]** で**プラットフォーム ツールセット**を Visual Studio 2017 のツールセットである **v141** に設定します。

1. プロジェクトを Windows 8.1 プロジェクトとしてビルドし、ビルド エラーを解決します。 この段階のすべてのエラーは、ビルド ツールとライブラリでの互換性に影響する変更点によるものと思われます。 コードに影響する可能性のある変更の詳細については、「[Visual C++ change history 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)」 (Visual C++ 2003 ～ 2015 での互換性に影響する変更点) を参照してください。

   プロジェクトが正常にビルドされたら、ユニバーサル Windows (Windows 10) に移植できます。

1. 空白のテンプレートを使用して、新しいユニバーサル Windows アプリ プロジェクトを作成します。 プロジェクトには既存のプロジェクトと同じ名前を付けられますが、そうするためには、プロジェクトが異なるディレクトリにある必要があります。

1. ソリューションを閉じてから、**Windows エクスプローラー**またはコマンド ラインを使用して、コード ファイル (拡張子は .cpp、.h、.xaml) を Windows 8.1 プロジェクトから、手順 1. で作成したプロジェクトのプロジェクト ファイル (.vcxproj) と同じフォルダーにコピーします。 Package.appxmanifest ファイルはコピーしないでください。Windows 8.1 のデスクトップと Phone のそれぞれ別のコードがある場合は、いずれかを選択して最初に移植します (もう一方に合わせて調整する場合は、後でいくつかの作業を行う必要があります)。 サブフォルダーとその内容を必ずコピーしてください。 メッセージが表示されたら、名前が重複するすべてのファイルを置換するよう選択します。

1. ソリューションを再度開き、プロジェクト ノードのショートカット メニューから **[追加]** 、 **[既存の項目]** の順に選択します。 既にプロジェクトの一部であるものを除いて、コピーしたすべてのファイルを選択します。

   すべてのサブフォルダーを確認し、必ず、そこにも同様にファイルを追加してください。

1. 使用していないプロジェクトと同じプロジェクト名を使っていない場合は、Package.appxmanifest ファイルを開き、**エントリ ポイント**を更新して、`App` クラスの名前空間の名前を反映します。

   Package.appxmanifest ファイル内の **[エントリ ポイント]** フィールドには、`App` クラスを含む名前空間が含まれている、`App` クラスのスコープを持つ名前が含まれています。 ユニバーサル Windows プロジェクトを作成するときに、名前空間はプロジェクトの名前に設定されます。 これが古いプロジェクトからコピーしたファイルの内容と異なる場合は、どちらか一方を更新して一致させる必要があります。

1. プロジェクトをビルドして、異なるバージョンの Windows SDK 間での互換性に影響する変更点が原因で発生したビルド エラーをすべて解決します。

1. ローカル デスクトップでプロジェクトを実行します。 配置エラーがないことと、アプリのレイアウトが適切であることと、デスクトップで正しく機能することを確認します。

1. Windows Phone 8.1 など、別のデバイス用の個別のコード ファイルと .xaml がある場合、このコードを確認し、標準的なデバイスと異なる点を特定します。 レイアウト内でのみ違いが生じている場合は、xaml で **Visual State Manager** を使用して、画面のサイズに応じて表示をカスタマイズすることができます。 その他の違いについては、次の #if ステートメントを使用して、コード内で条件のセクションを使用できます。

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

   これらのステートメントは、それぞれ、UWP アプリ、Windows Phone ストア アプリ、両方のアプリ、どちらでもないアプリ (クラシック Win32 デスクトップのみ) の順に適用されます。 これらのマクロは Windows SDK 8.1 以降でのみ使用可能です。それ以前のバージョンの Windows SDK を使用してコードをコンパイルする必要があるか、Windows 以外のプラットフォーム用にコンパイルする必要がある場合は、マクロが全く定義されないケースも考えられます。

1. アプリでサポートされるデバイスの種類ごとに、エミュレーターまたは物理デバイスでアプリを実行してデバッグします。 エミュレーターを実行するには、仮想マシンではなく、物理コンピューター上で Visual Studio を実行する必要があります。

## <a name="BK_81Component"></a> UWP への Windows 8.1 ランタイム コンポーネントの移植

DLL、または Windows 8.1 ストア アプリで既に動作している Windows ランタイム コンポーネントがある場合は、この手順を使用して、UWP と Windows 10 でコンポーネントまたは DLL を使用できます。 基本的な手順は、新しいプロジェクトを作成し、それにコードをコピーすることです。

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>UWP への Windows 8.1 ランタイム コンポーネントの移植

1. Visual Studio 2017 の **[新しいプロジェクト]** ダイアログ ボックスで、**Windows ユニバーサル** ノードを見つけます。 このノードが表示されない場合は、最初に [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) をインストールします。 **Windows ランタイム コンポーネント** のテンプレートを選択し、コンポーネントの名前を入力し、 **[OK]** ボタンをクリックします。 コンポーネントの名前は名前空間の名前として使用されるので、古いプロジェクトの名前空間と同じ名前を使用することもできます。 この場合は、古いプロジェクトとは別のフォルダーにプロジェクトを作成することが必要です。 別の名前を選択した場合は、生成されたコード ファイルの名前空間名を更新できます。

1. プロジェクトを閉じます。

1. 新しく作成されたプロジェクトに Windows 8.1 コンポーネントからのすべてのコード ファイル (.cpp、.h、.xaml など) をコピーします。 Package.appxmanifest ファイルをコピーしないでください。

1. ビルドし、異なるバージョンの Windows SDK 間での互換性に影響する変更点が原因で発生したエラーをすべて解決します。

## <a name="troubleshooting"></a>トラブルシューティング

コードを UWP に移植するプロセスで、さまざまなエラーが発生する可能性があります。 発生する可能性がある問題をいくつか以下に示します。

### <a name="project-configuration-issues"></a>プロジェクトの構成問題

以下のようなエラーが発生する可能性があります。

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

この場合、プロジェクトはユニバーサル Windows プロジェクトとしてビルドされません。 プロジェクト ファイルを調べ、プロジェクトを Windows ユニバーサル プロジェクトとして識別する適切な XML 要素があることを確認してください。 次の要素が存在する必要があります (ターゲット プラットフォームのバージョン番号が異なる場合があります)。

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

Visual Studio を使用して、新しい UWP のプロジェクトを作成した場合は、このエラーは表示されません。

## <a name="see-also"></a>関連項目

[Visual C++ 移植ガイド](../porting/porting-to-the-universal-windows-platform-cpp.md)<br/>
[ユニバーサル Windows プラットフォーム (UWP) 向けアプリの開発](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)