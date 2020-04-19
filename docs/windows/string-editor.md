---
title: 文字列エディター (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: 996e5f132e5cfa33c39c4cc3ddbeb692f41925bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514718"
---
# <a name="string-editor-c"></a>文字列エディター (C++)

文字列テーブルは、アプリケーションのすべての文字列の ID、値、キャプションの一覧が含まれる Windows リソースです。 たとえば、文字列テーブルにはステータス バーのプロンプトがあります。

アプリケーションの開発中、いくつかの文字列テーブルを使用できます (各言語または条件ごとに 1 つ)。 しかし、実行可能モジュールには、文字列テーブルは 1 つしかありません。 実行中のアプリケーションは、テーブルを異なる DLL に置く場合、複数の文字列テーブルを参照することができます。

文字列テーブルにより、簡単にアプリケーションを異なる言語にローカライズできるようになります。 すべての文字列が文字列テーブルにある場合、ソース コードを変更せずに、文字列 (およびその他のリソース) を変換することにより、アプリケーションをローカライズすることができます。 この状況は、ソースファイル内のさまざまな文字列を手動で検索して置換するよりも望ましい方法です。

> [!NOTE]
> Windows では、空の文字列テーブルを作成することはできません。 エントリなしの文字列テーブルを作成する場合、そのテーブルはリソース ファイルの保存時に自動的に削除されます。

## <a name="how-to"></a>方法

**文字列エディター**では、次のことが可能です。

### <a name="to-find-a-string-resource-in-the-string-table"></a>文字列テーブル内の文字列リソースを検索するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)のアイコンをダブルクリックして、文字列テーブルを開きます。

1. メニューにアクセスし**て [検索と置換**] を**編集** > し、 **[検索]** を選択します。

1. [**検索**する文字列] ボックスで、ドロップダウンリストから以前の検索文字列を選択するか、検索する文字列のキャプションテキストまたはリソース識別子を入力します。

1. **[検索]** オプションのいずれかを選択し、 **[次を検索]** を選択します。

> [!TIP]
> ファイルを検索するときに[正規表現](/visualstudio/ide/using-regular-expressions-in-visual-studio)を使用するには、 **[編集]** メニューの **[フォルダーを検索]** コマンドを使用します。
>
> 正規表現を入力してパターンに一致させるか、 **[検索する文字列]** ボックスの右側にあるボタンを選択して、通常の検索式の一覧を表示します。 この一覧から式を選択すると、[検索する文字列] ボックスの検索テキストとして置き換えられます。
>
> 正規表現を使用する場合は、次**のものを使用してください。[正規**表現] チェックボックスがオンになっています。

### <a name="to-add-or-delete-a-string-resource"></a>文字列リソースを追加または削除するには

文字列**エディター**を使用して、文字列テーブルにエントリをすばやく挿入したり、削除したりできます。 新しい文字列はテーブルの末尾に配置され、次に使用できる識別子が与えられます。 必要に応じて、[プロパティウィンドウ](/visualstudio/ide/reference/properties-window)の**ID**、**値**、または**キャプション**のプロパティを編集できます。

**文字列エディター**は、既に使用されている ID を使用しないようにします。 既に使用されている ID を選択すると、**文字列エディター**によって通知され、一般的な一意`IDS_STRING58113`の id が割り当てられます。たとえば、のようになります。

#### <a name="to-add-a-string-table-entry"></a>文字列テーブルエントリを追加するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)のアイコンをダブルクリックして、文字列テーブルを開きます。

1. 文字列テーブル内を右クリックし、 **[新しい文字列]** を選択します。

1. **文字列エディター**で、 **[id]** ドロップダウンリストから**id**を選択するか、直接の*id*を入力します。

1. 必要に応じて、**値**を編集します。

1. **キャプション**のエントリを入力します。

   > [!NOTE]
   > Windows の文字列テーブルでは、Null 文字列は許可されません。 文字列テーブルに null 文字列のエントリを作成すると、**このテーブルエントリに文字列を入力**するように求めるメッセージが表示されます。

#### <a name="to-delete-a-string-table-entry"></a>文字列テーブルのエントリを削除するには

削除するエントリを選択して、次のいずれかの操作を行います。

- メニューにアクセスして、 **[削除]** を**編集** > します。

- 削除する文字列を右クリックし、 **[削除]** を選択します。

- **Del**キーを押します。

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>あるリソーススクリプトファイルから別のリソーススクリプトファイルに文字列を移動するには

1. [両方の .rc ファイルの文字列テーブルを開き](../windows/how-to-create-a-resource-script-file.md)ます。

1. 移動する文字列を右クリックし、 **[切り取り]** を選択します。

1. [ターゲット**文字列エディター** ] ウィンドウにカーソルを置きます。

1. 文字列を移動する *.rc*ファイルで、を右クリックし、 **[貼り付け]** を選択します。

> [!NOTE]
> 移動した文字列の**id**または**値**が、コピー先のファイルの既存の**id**または**値**と競合する場合、その**id**または移動した文字列の**値**が変更されます。

### <a name="to-change-the-properties-of-a-string-resource"></a>文字列リソースのプロパティを変更するには

埋め込み先編集を使用して、 **ID**、**値**、**キャプション**の各プロパティを変更できます。

> [!NOTE]
>  [プロパティウィンドウ](/visualstudio/ide/reference/properties-window)で文字列のプロパティを編集することもできます。

#### <a name="to-change-a-string-or-its-identifier"></a>文字列またはその識別子を変更するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)のアイコンをダブルクリックして、文字列テーブルを開きます。

1. 編集する文字列を選択し、 **[ID]** 、 **[値]** 、または **[キャプション]** 列をダブルクリックすると、次のことができます。

   - **[Id]** ドロップダウンリストから**id**を選択するか、適切な場所に*id*を直接入力します。

   - **値**列に別の数値を入力します。

   - **キャプション**列に「編集」と入力します。

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>複数の文字列リソースの caption プロパティを変更するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)のアイコンをダブルクリックして、文字列テーブルを開きます。

1. **Ctrl**キーを押しながら各文字列を選択することによって、変更する文字列を選択します。

1. [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で、変更するプロパティの新しい値を入力します。

1. **Enter** キーを押します。

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>文字列リソースに書式設定または特殊文字を追加するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)のアイコンをダブルクリックして、文字列テーブルを開きます。

1. 変更する文字列を選択します。

1. [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で、次に示す標準的なエスケープシーケンスを **[キャプション]** ボックスのテキストに追加し、enter キーを押します。

   |これを取得するには...|次のように入力します。|
   |-----------------|---------------|
   | 改行 | \\非該当 |
   | キャリッジ リターン | \\\r\n\r\n |
   | タブ | \\t |
   | 円記号 (\\) | \\\\ |
   | ASCII 文字 | \\ddd (8 進数表記) |
   | アラート (ベル) | \\a |

   > [!NOTE]
   > **文字列エディター**は、エスケープされた asci 文字の完全なセットをサポートしていません。 使用できるのは上記の一覧のみです。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソースエディター](../windows/resource-editors.md)
の[文字列](/windows/win32/menurc/strings)<br/>
[文字列の概要](/windows/win32/menurc/about-strings)<br/>
[ウィンドウ レイアウトをカスタマイズする](/visualstudio/ide/customizing-window-layouts-in-visual-studio)