---
title: Linux プロジェクトを構成してアドレス サニタイザーを使用する
description: Visual Studio で C++ の Linux プロジェクトを構成して、アドレス サニタイザーを使用する方法について説明します。
ms.date: 06/07/2019
ms.openlocfilehash: da7197981a431becfc1231dae96f7542062de675
ms.sourcegitcommit: b3d19b5f59f3a5d90c24f9f16c73bad4c5eb6944
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195868"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Linux プロジェクトを構成してアドレス サニタイザーを使用する

Visual Studio 2019 バージョン 16.1 の Linux プロジェクトには、AddressSanitizer (ASan) のサポートが統合されています。 ASan は、MSBuild ベースの Linux プロジェクトおよび CMake プロジェクトの両方で有効にできます。 これは、リモートの Linux システムおよび Windows Subsystem for Linux (WSL) で動作します。

## <a name="about-asan"></a>ASan とは

ASan とは、C/C++ の次のエラーを検出する、ランタイム メモリ エラー検出機能です。

- 解放済みへの操作 (付随的なポインターの参照)
- ヒープのバッファー オーバーフロー
- スタックのバッファー オーバーフロー
- 関数外からの操作
- スコープ外からの操作
- 初期化順序のバグ

ASan がエラーを検出すると、すぐに実行が停止されます。 デバッガーで ASan が有効になっているプログラムを実行すると、エラーの種類、メモリ アドレス、およびエラーが発生したソース ファイル内の場所を説明するメッセージが表示されます。

   ![ASan のエラー メッセージ](media/asan-error.png)

ASan の (破損したメモリが割り当てられているまたは割り当て解除されている場所を含む) すべての出力は、出力ウィンドウの [デバッグ] ウィンドウでも確認できます。

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>MSBuild ベースの Linux プロジェクトで ASan を有効にする

> [!NOTE]
> Visual Studio 2019 バージョン 16.4 以降では、Linux プロジェクト用の AddressSanitizer は **[構成プロパティ]**  >  **[C/C++]**  >  **[Address Sanitizer を有効にする]** を使って有効にします。

ASan を MSBuild ベースの Linux プロジェクトで有効にするには、そのプロジェクトを**ソリューション エクスプローラー**で右クリックし、 **[プロパティ]** を選択します。 次に **[構成プロパティ]**  >  **[C/C++]**  >  **[サニタイザー]** の順に移動します。 ASan はコンパイラとリンカー フラグから有効にし、プロジェクトを再コンパイルして動作するようにします。

![MSBuild プロジェクトで ASan を有効にする](media/msbuild-asan-prop-page.png)

オプションの ASan ランタイム フラグを渡すには、 **[構成プロパティ]**  >  **[デバッグ]**  >  **[AddressSanitizer ランタイム フラグ]** に移動します。 下向き矢印をクリックし、フラグを追加または削除します。

![ASan ランタイム フラグを構成する](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Visual Studio の CMake プロジェクトで ASan を有効にする

CMake で ASan を有効にするには、**ソリューション エクスプローラー**の CMakeLists.txt ファイルを右クリックし、 **[CMake Settings for Project]** \(プロジェクトの CMake 設定\) を選択します。

ダイアログ ボックスの左ウィンドウで、(「**Linux-Debug**」などの) Linux の構成が選択されていることを確認します。

![Linux のデバッグ構成](media/linux-debug-configuration.png)

ASan のオプションは **[全般]** の下にあります。 ASan ランタイム フラグは、セミコロンで区切って "フラグ=値" の形式で入力します。

![Linux のデバッグ構成](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>ASan のデバッグ シンボルをインストールする

ASan の診断を有効にするには、リモート Linux マシンまたは WSL インストールにそのデバッグ シンボル (libasan-dbg) をインストールする必要があります。 読み込む libasan-dbg のバージョンは、お使いの Linux マシンにインストールされている GCC のバージョンによって異なります。

|**ASan のバージョン**|**GCC のバージョン**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

このコマンドを使用すると、どのバージョンの GCC を所有しているか特定できます。

```bash
gcc --version
```

必要な libasan-dbg のバージョンを確認するには、プログラムを実行し、 **[出力]** ウィンドウの **[デバッグ]** ウィンドウを確認します。 読み込まれている ASan のバージョンは、お使いの Linux マシンに必要な libasan-dbg のバージョンと対応しています。 **Ctrl + F** を使用し、ウィンドウで「libasan」を検索します。 たとえば Libasan4 がインストールされている場合、次のような行が表示されます。

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

次のコマンドを使用すると、Linux ディストリビューションに apt を使用する ASan デバッグ ビットをインストールできます。 このコマンドでは、バージョン 4 がインストールされます。

```bash
sudo apt-get install libasan4-dbg
```

ASan が有効な場合、Visual Studio の **[出力]** ウィンドウの **[デバッグ]** ウィンドウの上部で、ASan のデバッグ シンボルをインストールするよう求められます。
