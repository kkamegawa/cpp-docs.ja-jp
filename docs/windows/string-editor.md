---
title: 文字列エディター (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 24e4e6ba5b9c2dff1a179bea39830f4a3bbe5879
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702981"
---
# <a name="string-editor-c"></a>文字列エディター (C++)

文字列テーブルは、アプリケーションのすべての文字列の ID、値、キャプションの一覧が含まれる Windows リソースです。 たとえば、文字列テーブルにはステータス バーのプロンプトがあります。

アプリケーションの開発中、いくつかの文字列テーブルを使用できます (各言語または条件ごとに 1 つ)。 しかし、実行可能モジュールには、文字列テーブルは 1 つしかありません。 実行中のアプリケーションは、テーブルを異なる DLL に置く場合、複数の文字列テーブルを参照することができます。

文字列テーブルにより、簡単にアプリケーションを異なる言語にローカライズできるようになります。 すべての文字列が文字列テーブルにある場合、ソース コードを変更せずに、文字列 (およびその他のリソース) を変換することにより、アプリケーションをローカライズすることができます。 このような状況が手動での検索とソース ファイル内のさまざまな文字列を置換するよりも高くなります。

マネージ プロジェクト (共通言語ランタイムを対象とするプロジェクト) にリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列をプロパティに割り当てる方法については、次を参照してください。[チュートリアル。Windows フォームのローカリゼーション](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)します。

使用して、**文字列**エディターは、次のアクション。

## <a name="to-find-a-string-resource-in-the-string-table"></a>文字列テーブル内の文字列リソースを検索するには

文字列テーブル内 1 つまたは複数の文字列を検索して使用することができます[正規](/visualstudio/ide/using-regular-expressions-in-visual-studio)で、**ファイル内の検索**コマンド (**編集**メニュー) 文字列のすべてのインスタンスを検索するにはパターンに一致します。

1. アイコンをダブルクリックして、文字列テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. **編集**メニューの **検索し、置換**を選択し、**検索**します。

1. **検索**ボックス、ドロップダウン リストから、以前の検索文字列を選択または検索する文字列のキャプション テキストまたはリソース識別子を入力します。

1. いずれかの選択、**検索**オプション。

1. 選択**次を検索**します。

   > [!TIP]
   > ファイルを検索するときに正規表現を使用する、**ファイル内の検索**コマンド。 正規表現パターンに一致またはの右側にボタンを選択する、**検索**検索の正規表現の一覧を表示するボックスです。 この一覧から式を選択すると、検索文字列として設定されます、**検索**ボックス。 正規表現を使用する場合は必ず、**を使用します。正規表現** チェック ボックスをオンします。

## <a name="to-add-or-delete-a-string-resource"></a>追加または文字列リソースを削除するには

すぐに挿入したり、文字列を使用してテーブルにエントリを削除できます、**文字列**エディター。 新しい文字列は、テーブルの末尾に配置され、[次へ] の使用可能な識別子が与えられます。 編集することができます、 **ID**、**値**、または**キャプション**プロパティで、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)に応じて。

**文字列**エディターでは、既に使用されている ID を使用しないでください。 ID を既に使用して、選択した場合、**文字列**エディターは通知し、たとえば一般的な一意の ID を割り当てる`IDS_STRING58113`します。

### <a name="to-add-a-string-table-entry"></a>ストリング テーブルのエントリを追加するには

1. アイコンをダブルクリックして、文字列テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. 文字列テーブル内で右クリックし、**新しい文字列**ショートカット メニューから。

1. **文字列**エディターで、 **ID**からドロップダウン リストの ID または ID で直接の場所の種類。

1. 編集、**値**、必要な場合。

1. エントリを入力、**キャプション**します。

   > [!NOTE]
   > Null 文字列は、Windows ストリング テーブルでは許可されません。 「を入力してください、文字列のこのテーブルのエントリ」を選択するメッセージが表示されます、null 文字列である文字列テーブルにエントリを作成する場合

### <a name="to-delete-a-string-table-entry"></a>文字列テーブルのエントリを削除するには

1. 削除するエントリを選択します

1. **編集**メニューの **削除**します。

\- または -

 削除する文字列を右クリックして**削除**ショートカット メニューから。

\- または -

 キーを押して、**削除**キー。

## <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>文字列を別の 1 つのリソース スクリプト ファイルに移動するには

1. 両方の .rc ファイルでは、文字列テーブルを開きます。 (詳細については、次を参照してください[を表示するリソースで、リソース スクリプト ファイル プロジェクトの外側に](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。)。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. を選択する文字列を右クリックして**切り取り**ショートカット メニューから。

1. ターゲットにカーソルを置き**文字列エディター**ウィンドウ。

1. 文字列を移動する .rc ファイルを右クリックし、選択**貼り付け**ショートカット メニューから。

   > [!NOTE]
   > 場合、 **ID**または**値**既存の文字列の移動の競合の**ID**または**値**変換先のファイルか、 **ID**または**値**の移動先の文字列を変更します。 同じ文字列が存在する場合は**ID**、 **ID**の移動先の文字列の変更。 同じ文字列が存在する場合は**値**、**値**の移動先の文字列の変更。

## <a name="to-change-the-properties-of-a-string-resource"></a>文字列リソースのプロパティを変更するには

ID、値、およびキャプションのプロパティを変更するには、インプレース編集を使用します。

### <a name="to-change-a-string-or-its-identifier"></a>文字列または識別子を変更するには

1. アイコンをダブルクリックして、文字列テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

2. 編集するをダブルクリックする文字列を選択、 **ID**、**値**、または**キャプション**列。 これで次のようなことができます。

   - 選択、 **ID**から、 **ID ドロップダウン**リスト、または型、`ID`は直接します。

   - 別の番号を入力、**値**列。

   - 入力時に編集、**キャプション**列。

        > [!NOTE]
        >  文字列のプロパティを編集することも、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。

### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>複数の文字列リソースの caption プロパティを変更するには

1. アイコンをダブルクリックして、文字列テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. 押しながら変更する文字列を選択、 **Ctrl**キーの 1 つを選択するとします。

1. [プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)、変更するプロパティの新しい値を入力します。

1. **Enter** キーを押します。

## <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>文字列リソースへの書式設定や特殊文字を追加するには

1. アイコンをダブルクリックして、文字列テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. 変更する文字列を選択します。

1. [プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)、内のテキストには以下の標準のエスケープ シーケンスのいずれかの追加、**キャプション**ボックスで、キーを押します**Enter**します。

   |これを取得するには|入力します。|
   |-----------------|---------------|
   | 改行 | \\n |
   | キャリッジ リターン | \\r |
   | タブ | \\t |
   | 円記号 (\\) | \\\\ |
   | ASCII 文字 | \\ddd (8 進表記) |
   | 警告 (ベル) | \\a |

> [!NOTE]
> **文字列**エディターが ASCI のエスケープ文字の完全なセットをサポートしていません。 上記のリストにのみ使用できます。

> [!NOTE]
> Windows では、空の文字列テーブルを作成することができません。 エントリなしの文字列テーブルを作成する場合、そのテーブルはリソース ファイルの保存時に自動的に削除されます。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース エディター](../windows/resource-editors.md)<br/>
[リソース ファイル](../windows/resource-files-visual-studio.md)<br/>
[文字列](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[文字列の概要](/windows/desktop/menurc/about-strings)<br/>
[ウィンドウ レイアウトをカスタマイズする](/visualstudio/ide/customizing-window-layouts-in-visual-studio)