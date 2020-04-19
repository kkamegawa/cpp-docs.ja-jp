---
title: '方法: リソースは、コンパイル時 (C++)'
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: ca24a10f905e61feb2b090ba3966c752db3d4444
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350924"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>方法: リソースは、コンパイル時 (C++)

既定ですべてのリソースが 1 つのリソース スクリプト (.rc) ファイル内にある、ただしはメインの .rc ファイル以外のファイルにリソースを配置する多くの理由。

- .Rc ファイルを保存するときに削除されないリソース ステートメントには、コメントを追加します。

- リソースが既に開発し、テストをインクルードして、さらに変更の必要はありません。 含まれていますが、.rc 拡張子を持っていないすべてのファイルは、リソース エディターで編集することはできません。

- 別のプロジェクトで使用されているか、ソース コードのバージョン管理システムの一部であるリソースを含める。 これらのリソースは、変更がすべてのプロジェクトに影響は、中央の場所に存在する必要があります。

- カスタム形式である (RCDATA リソース) などのリソースが含まれます。 RCDATA リソースの値として式を使用することはできません、特別な要件がある、`nameID`フィールド。

いずれかでこれらのセクションの配置をこれらの条件のいずれかを満たす既存の .rc ファイルでセクションがある場合または別個の .rc ファイルの詳細、およびそれらを使用して、プロジェクトに含める、**リソース ファイルのインクルード** ダイアログ ボックス。

## <a name="resource-includes"></a>リソースが含まれています

追加できますリソースその他のファイルをプロジェクトにコンパイル時にそれらを一覧表示して、**コンパイル時ディレクティブ**ボックスに、**リソースが含まれています** ダイアログ ボックス。 使用して、**リソースが含まれています**プロジェクト環境の通常の作業配置プロジェクトの .rc ファイル内のすべてのリソースを格納するを変更する ダイアログ ボックス[シンボル](../windows/symbols-resource-identifiers.md)で`Resource.h`します。

最初に、開く、**リソースが含まれています** ダイアログ ボックスで、.rc ファイルを右クリックして[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)を選択します**リソースが含まれています**と次のプロパティ。

| プロパティ | 説明 |
|---|---|
| **シンボル ヘッダー ファイル** | リソース ファイルのシンボル定義が格納されているヘッダー ファイルの名前を変更することができます。<br/><br/>詳細については、次を参照してください。[シンボル ヘッダー ファイルの名前を変更する](../windows/changing-the-names-of-symbol-header-files.md)します。 |
| **読み取り専用シンボル ディレクティブ** | 変更しないでくださいシンボルが含まれているヘッダー ファイルをインクルードできます。<br/><br/>たとえば、シンボル ファイルを共有する他のプロジェクトとします。 MFC の .h ファイルを含めることもできます。 詳細については、次を参照してください。[共有 (読み取り専用) または計算型シンボル](../windows/including-shared-read-only-or-calculated-symbols.md)します。 |
| **コンパイル時ディレクティブ** | 作成され、メイン リソース ファイル内のリソースから個別に編集されているリソース ファイルを含めることができます (など、それらのディレクティブを条件付きでリソースを含む)、コンパイル時ディレクティブを含めることがまたは、カスタム形式でリソースが含まれます。<br/><br/>使用することも、**コンパイル時ディレクティブ ボックス**標準 MFC リソース ファイルをインクルードします。 |

> [!NOTE]
> マークされた .rc ファイルにこれらのテキスト ボックス内のエントリが表示される`TEXTINCLUDE 1`、 `TEXTINCLUDE 2`、および`TEXTINCLUDE 3`それぞれします。 詳細については、次を参照してください[TN035:。複数のリソース ファイルとヘッダー ファイルを使用して、Visual C を使った](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)します。

リソース ファイルを使用して変更を加えたら、**リソースが含まれています**ダイアログ ボックスで、必要がありますを閉じて、 *.rc*ファイルの変更を有効にします。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>コンパイル時にリソースをインクルードするには

1. 一意のファイル名を持つリソース スクリプト ファイルにリソースを配置します。 使用しない*projectname.rc*、これは、メイン リソース スクリプト ファイルを使用しているファイルの名前です。

1. 右クリックし、 *.rc*ファイル[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)選択**リソースが含まれています**します。

1. **コンパイル時ディレクティブ**ボックスで、追加、 [#include](../preprocessor/hash-include-directive-c-cpp.md)開発環境で、メイン リソース ファイルで新しいリソース ファイルをインクルードします。

この方法に含まれるファイル内のリソースは、コンパイル時に実行可能ファイルの一部となるのみと、プロジェクトのメイン .rc ファイルでの作業と編集または変更に使用できません。 インクルードされる .rc ファイルを個別に開かれている必要があり、.rc 拡張子を付けずに含まれるすべてのファイルは、リソース エディターで編集できません。

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>指定する特定のリソース (.rc) ファイルのインクルード ディレクトリ

1. 右クリックし、 *.rc*ファイル**ソリューション エクスプ ローラー**選択**プロパティ**します。

1. 選択、**リソース**左側のウィンドウでノード追加を指定し、インクルード ディレクトリで、**追加のインクルード ディレクトリ**プロパティ。

### <a name="to-find-symbols-in-resources"></a>リソース内のシンボルを検索するには

1. メニューに移動して**編集** > [シンボルの検索](/visualstudio/ide/go-to)します。

   > [!TIP]
   > 使用する[正規](/visualstudio/ide/using-regular-expressions-in-visual-studio)は検索に次のように選択します。[ファイル内の検索](/visualstudio/ide/reference/find-command)で、**編集**の代わりにメニュー**シンボルの検索**します。 選択、**使用。正規表現** チェック ボックス、[検索 ダイアログ ボックス](/visualstudio/ide/finding-and-replacing-text)し、**検索**ボックスのドロップダウン リストから検索の正規表現を選択することができます。 この一覧から式を選択すると、検索文字列として設定されます、**検索**ボックス。

1. **検索**ボックスで、ドロップダウン リストから、以前の検索文字列を選択するかなどを検索するアクセラレータ キーを入力`ID_ACCEL1`します。

1. いずれかの選択、**検索**オプションし、選択**次を検索**します。

> [!NOTE]
> 文字列リソース、アクセラレータ リソース、またはバイナリ リソース内のシンボルは検索できません。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース ファイル](../windows/resource-files-visual-studio.md)<br/>
[方法: リソースの作成](../windows/how-to-create-a-resource-script-file.md)<br/>
[方法: リソースの管理](../windows/how-to-copy-resources.md)<br/>