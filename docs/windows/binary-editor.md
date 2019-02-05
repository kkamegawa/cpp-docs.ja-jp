---
title: バイナリ エディター (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 06c4a224b745f5aba8c9105d32489f8ca3109e1c
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293599"
---
# <a name="binary-editor-c"></a>バイナリ エディター (C++)

> [!WARNING]
> **バイナリ エディター** Express エディションでは使用できません。

バイナリ エディターを使うと、16 進形式または ASCII 形式を使用してバイナリ レベルでリソースを編集できます。 また、 [[検索] コマンド](/visualstudio/ide/reference/find-command) を使うと、ASCII 文字列や 16 進表現のバイト列を検索できます。 使用する必要があります、**バイナリ**カスタム リソースや、Visual Studio 環境でサポートされていないリソースの種類のエディターを表示またはマイナー必要がある場合にのみ変更します。

開くには、**バイナリ エディター**、最初に選択**ファイル** > **新規** > **ファイル**メイン メニューで、次のように選択します、。ファイルを編集し、横にドロップダウン矢印をクリックする、**オープン**ボタンをクリックし、選択**プログラムから開く** > **バイナリ エディター**します。

> [!CAUTION]
> ダイアログ ボックス、イメージ、メニューなどのリソースをバイナリ エディターで編集することは危険です。 編集方法が正しくないと、リソースを破損し、本来のエディターで読み取ることができなくなる場合があります。

> [!TIP]
> 使用しているときに、**バイナリ**多くの場合、エディターを右クリック リソース固有のコマンドのショートカット メニューを表示します。 使用できるコマンドは、ポインターの位置によって異なります。 たとえばをポイントした状態をクリックする、**バイナリ**16 進値が選択されているエディター、ショートカット メニューを示しています、**切り取り**、**コピー**と**貼り付け**コマンド。

## <a name="binary-editor-how-to"></a>バイナリ エディターに関する「方法」

**バイナリ**エディターは、次の操作を参照してください。

### <a name="to-open-a-resource-for-binary-editing"></a>バイナリ編集するためのリソースを開く

#### <a name="to-open-a-windows-desktop-resource"></a>Windows デスクトップ リソースを開く

1. [リソース ビュー](../windows/resource-view-window.md)で、編集の対象となる特定のリソース ファイルを選択します。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. リソースを右クリックし、ショートカット メニューから **[バイナリー データを開く]** をクリックします。

   > [!NOTE]
   > 使用する場合、[リソース ビュー](../windows/resource-view-window.md)で Visual Studio が認識しないこと (RCDATA やカスタム リソース) など、リソースの形式でリソースを開くウィンドウが自動的に開きます、**バイナリ**エディター。

#### <a name="to-open-a-managed-resource"></a>マネージ リソースを開く

1. **ソリューション エクスプ ローラー**、編集する特定のリソース ファイルを選択します。

1. リソースを右クリックして、ショートカット メニューから **[プログラムから開く]** を選択します。

1. **[プログラムから開く]** ダイアログ ボックスで、 **バイナリ エディター**を選択します。

   > [!NOTE]
   > [イメージ エディター](../windows/image-editor-for-icons.md) と [バイナリ エディター](binary-editor.md) を使用して、マネージド プロジェクトのリソース ファイルを操作できます。 編集の対象となるマネージド リソースは、リンク リソースである必要があります。 Visual Studio のリソース エディターでは、埋め込みリソースの編集はサポートしていません。

![バイナリ エディター](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
バイナリ エディターに表示されるダイアログ ボックスのバイナリ データ

バイナリ エディターでは、特定の ASCII 値のみが表されます (0x20 ～ 0x7E)。 拡張文字は、バイナリ エディターの ASCII 値セクション (右側のパネル) にピリオドで表示されます。 "印刷可能" な文字は、ASCII 値の 32 ～ 126 です。

> [!NOTE]
> 使用する場合、**バイナリ**別のエディター ウィンドウで既に編集中のリソース エディターが最初に他のエディター ウィンドウを閉じます。

### <a name="to-edit-a-resource-in-the-binary-editor"></a>バイナリ エディターでのリソースを編集するには

1. 編集するバイトを選択します。

   **タブ**キーは、16 進数のセクションでは ASCII とフォーカスを移動、**バイナリ**エディター。 使用することができます、 **Pageup**と**Pagedown**一度にリソースの 1 つの画面を移動するキー。

1. 新しい値を入力します。

   値は 16 進数と ASCII セクションの両方ですぐに変更し、行の次の値にフォーカスを移動します。

   > [!NOTE]
   > **バイナリ**エディターの変更を受け入れます自動的に、エディターを閉じるときにします。

### <a name="to-find-binary-data"></a>バイナリ データを検索するには

ASCII 文字列や 16 進数のバイトのいずれかを検索することができます。 たとえば、「こんにちは」を検索することができますまたは検索するいずれかの文字列「こんにちは」"48 65 6C 6c 6F"(16 進数に相当)。

1. **編集**] メニューの [選択[検索](/visualstudio/ide/reference/find-command)します。

1. **検索**ボックス、ドロップダウン リストから、以前の検索文字列を選択または検索するデータを入力します。

1. いずれかの選択、**検索**オプション。

1. 選択**次を検索**します。

### <a name="to-create-a-new-custom-or-data-resource"></a>新しいカスタム リソースやデータ リソースを作成するには

プロジェクトを右クリックして通常のリソース スクリプト (.rc) ファイルの構文を使用して別のファイルに、そのファイルをインクルードし、リソースを配置して、新しいカスタム リソースやデータ リソースを作成する**ソリューション エクスプ ローラー** ]をクリック**リソースが含まれます**ショートカット メニューの [します。

1. カスタム リソースやデータ リソースが格納される[.rc ファイルを作成します](../windows/how-to-create-a-resource-script-file.md) 。

   null で終わる引用符で囲まれた文字列として、または 10 進数、16 進数、または 8 進数形式の整数として.rc ファイルにカスタム データを入力することができます。

1. **ソリューション エクスプローラー**でプロジェクトの .rc ファイルを右クリックし、ショートカット メニューの **[リソース ファイルのインクルード]** をクリックします。

1. **コンパイル時ディレクティブ**ボックスに、入力、`#include`カスタム リソースを含むファイルの名前を指定するステートメント。 例:

    ```cpp
    #include mydata.rc
    ```

   入力する構文とスペルが正しいことを確認します。 **[コンパイル時に追加するファイル]** ボックスの内容が、入力したとおりにリソース スクリプト ファイルに挿入されます。

1. 選択**OK**変更内容を記録します。

カスタム リソースを作成する別の方法として、外部ファイルをカスタム リソースとしてインポートする方法もあります。 詳細については、「 [リソースのインポートとエクスポート](../windows/how-to-import-and-export-resources.md)」を参照してください。

> [!NOTE]
> 新しいカスタム リソースまたはデータ リソースを作成するには、Win32 が必要です。

## <a name="managed-resources"></a>マネージド リソース

使用することができます、[イメージ エディター](../windows/image-editor-for-icons.md)と**バイナリ**マネージ プロジェクトのエディターでのリソース ファイルを操作します。 編集の対象となるマネージド リソースは、リンク リソースである必要があります。 Visual Studio のリソース エディターでは、埋め込みリソースの編集はサポートしていません。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[リソース エディター](../windows/resource-editors.md)