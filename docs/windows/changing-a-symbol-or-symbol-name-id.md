---
title: '方法: シンボルを管理します。'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: ebf10ade734d321c5a83644110d3511e4b6c827a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406978"
---
# <a name="how-to-manage-symbols"></a>方法: シンボルを管理します。

新しいリソースまたはリソース オブジェクトを作成するときに、開発環境によって割り当てられます既定のシンボル名では、たとえば、`IDD_DIALOG1`します。 使用することができます、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)を既定のシンボル名を変更する、またはリソースに既に関連付けられている任意のシンボルの名前を変更します。

1 つのリソースに関連付けられているシンボルを使用することも、**プロパティ**シンボル値を変更するウィンドウ。 使用することができます、[リソース シンボル ダイアログ ボックス](../windows/resource-symbols-dialog-box.md)リソースに割り当てられていないシンボルの値を変更します。

通常、すべてのシンボルが定義に保存`Resource.h`します。 ただし、同じディレクトリ内の複数のリソース ファイルを使用する場合などに、このインクルード ファイル名の変更が必要になることがあります。

> [!NOTE]
> 場合は、プロジェクトに .rc ファイル含まれていないを参照してください。[方法。リソースを作成する](../windows/how-to-create-a-resource-script-file.md)します。

## <a name="symbol-name-restrictions"></a>シンボル名の制限

シンボル名に関する制限は、次のとおりです。

- すべて[シンボル](../windows/symbols-resource-identifiers.md)をヘッダー ファイル内のシンボル定義の競合を防ぐために、アプリケーションのスコープ内で一意である必要があります。

- シンボル名で有効な文字は、A ～ Z、a ～ z、0 ～ 9、およびアンダー スコア (_) です。

- シンボル名を数字で始めることはできませんし、247 文字に制限されています。

- シンボル名は、スペースを含めることはできません。

- シンボル名は大文字小文字が区別されませんが、最初のシンボル定義の大文字と小文字は保持されます。

   シンボルを定義するヘッダー ファイルは、リソース ファイルで定義されているリソースを参照するために、リソース コンパイラ/エディターと C++ プログラムの両方で使用されます。 大文字か小文字かだけが異なる 2 つのシンボル名の場合、C++ プログラムは 2 つの個別のシンボルと見なしますが、リソース コンパイラ/エディターはどちらの名前も 1 つのシンボルを指していると見なします。

> [!NOTE]
> 標準のシンボル名スキームに従っていない場合 (従わずし、見かけ上はランダム エラーの生成でリソース スクリプト ファイルをビルドしようとしていますリソース スクリプト コンパイラで認識されるキーワードの結果として、同じである、シンボル名が起こるか。診断は困難なです。 これを回避するには、標準名前付けスキームに従います。

シンボル名には説明的なプレフィックスがあり、対象となるリソースやオブジェクトの種類を示します。 これらの説明的なプレフィックスは、テキストを組み合わせた ID で始まります。 Microsoft Foundation Class (MFC) ライブラリでは、名前付け規則は、次の表に示すようにシンボルを使用します。

|カテゴリ|プレフィックス|用途|
|--------------|------------|---------|
|リソース|IDR _、IDD _、IDC _、IDI_ IDB_|アクセラレータまたはメニュー (および関連付けられているかカスタム リソース) ダイアログ ボックス、カーソル、アイコン、ビットマップ|
|メニュー項目|ID_|メニュー項目|
|コマンド|ID_|コマンド|
|コントロールと子ウィンドウ|IDC_|コントロール|
|文字列|IDS_|文字列テーブル内の文字列|
|MFC|AFX_|定義済みの MFC シンボル用に予約されています|

### <a name="to-change-a-symbol-name-id"></a>シンボル名 (ID) を変更するには

1. [リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)リソースを選択します。

1. **プロパティ**ウィンドウで、新しいシンボル名を入力するか既存のシンボルの一覧から選択、 **ID**ボックス。

   新しいシンボル名を入力する場合、値が割り当てに自動的にします。

> [!NOTE]
> 使用することができます、[リソース シンボル ダイアログ ボックス](../windows/resource-symbols-dialog-box.md)リソースに割り当てられていないシンボルの名前を変更します。

## <a name="symbol-value-restrictions"></a>シンボル値の制限

シンボル値の通常の方法で表現される整数を指定できます`#define`プリプロセッサ ディレクティブです。 シンボル値の例をいくつか次に示します。

```
18
4001
0x0012
-3456
```

アクセラレータ、ビットマップ、カーソル、ダイアログ ボックス、アイコン、メニューの文字列テーブル、およびバージョンについては、0 ~ 32,767 の範囲の 10 進数である必要がありますが、16 進数にすることはできませんなどのリソースのシンボル値です。 一部のリソース (ダイアログ ボックスのコントロールや文字列テーブルの個々の文字列など) のシンボル値には、0 ～ 65,534 または、-32,768 ～ 32,767 の範囲の値を使用できます。 数値の範囲の詳細については、次を参照してください[TN023:。標準 MFC リソース](../mfc/tn023-standard-mfc-resources.md)します。

リソース シンボルは、16 ビットの数値です。 符号付きまたは符号なしとして入力することがあります、ただし、いる使用内部的には、符号なし整数としてため、負の数値は、対応する正の値にキャストされます。

シンボル値のいくつかの制限は次のとおりです。

- Visual Studio 開発環境と MFC では、特殊な目的でいくつかの数値の範囲を使用しています。 最上位ビットが設定されたすべての数値 (符号に応じて -32,768 ～ -1 または 32,768 ～ 65,534) は MFC によって予約されています。

- その他の記号文字列を使用してシンボル値を定義することはできません。 たとえば、次のシンボル定義はサポートされていません。

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- プリプロセッサ マクロは、値の定義として引数を使用できません。 次の例では、何に関係なく、有効な式のない`ID`コンパイル時に評価されます。

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- アプリケーションには、式を使用して定義されたシンボルを含む既存のファイルが存在する可能性があります。

### <a name="to-change-a-symbol-value"></a>シンボル値を変更するには

1. [リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)リソースを選択します。

1. **プロパティ**ウィンドウで、型、シンボル名の後に等号 (=)、整数の**ID**ボックスで、たとえば。

    ```
    IDC_EDITNAME=5100
    ```

   新しい値は、次回のプロジェクトの保存時に、シンボル ヘッダー ファイルに格納されます。 [ID] ボックスで、シンボル名だけが表示されると、検証している後に等号と値は表示されません。

## <a name="change-or-delete-symbols"></a>変更または削除記号

[リソース シンボル ダイアログ ボックス](../windows/resource-symbols-dialog-box.md)、編集またはリソースまたはオブジェクトに既に割り当てられていない既存のシンボルを削除することができます。

### <a name="to-change-an-unassigned-symbol"></a>未使用のシンボルを変更するには

1. **名前**ボックスで未使用のシンボルを選択し、選択**変更**します。

1. シンボルの名前またはで用意されているボックス内の値を編集、**シンボルの変更** ダイアログ ボックス。

> [!NOTE]
> リソースまたはオブジェクトに割り当てられているシンボルを変更するには、リソース エディターを使用する必要がありますまたは**プロパティ**ウィンドウ。

### <a name="to-delete-an-unassigned-unused-symbol"></a>割り当てられていない (使用されていない) シンボルを削除するには

**リソース シンボル** ダイアログ ボックスで、削除、および選択する記号を選択して**削除**します。

> [!NOTE]
> リソース ファイル内の未使用のシンボルを削除する前に、または使用されていない他の場所でプログラムのコンパイル時に含まれるリソース ファイルを確認します。

## <a name="include-symbols"></a>シンボルを含める

別のアプリケーションによって作成されたリソース ファイルを開発環境に初めて読み取るとき、インクルードされるすべてのヘッダー ファイルが読み取り専用とマークされます。 使用することができますが、 [] ダイアログ ボックスの [リソース インクルード](../windows/resource-includes-dialog-box.md)追加の読み取り専用シンボル ヘッダー ファイルを追加します。

読み取り専用のシンボル定義を使用する状況の 1 つに、複数のプロジェクト間でシンボル ファイルを共有する場合があります。

インクルードされるシンボル ファイルは、単純な整数の代わりに式を使用してシンボル値を定義するシンボル定義を含む既存のリソースがあるときに使用することもできます。 例:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

計算型シンボルは、次の条件が満たされる場合に環境によって適切に解釈されます。

- 計算型シンボルが読み取り専用シンボル ファイルに配置されている。

- これらの計算型シンボルが既に割り当てられているリソースがリソース ファイルに含まれている。

- 数値式が求められる。

> [!NOTE]
> 文字列または数値式が求められる場合、式は評価されません。

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>共有 (読み取り専用) シンボルをリソース ファイルに含めるには

1. [リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)を右クリックし、 *.rc*ファイルおよび選択[リソースが含まれています](../windows/resource-includes-dialog-box.md)します。

1. **読み取り専用シンボル ディレクティブ**ボックスで使用して、`#include`コンパイラ ディレクティブをファイルの読み取り専用のシンボルを格納する場所を指定します。

   ファイルを呼び出さないでください`Resource.h`、通常、メイン シンボル ヘッダー ファイルで使用されるファイル名があるためです。

   > [!NOTE]
   > 入力する、**読み取り専用シンボル ディレクティブ**ボックスが入力したとおりにリソース ファイルに含まれています。 入力ミスや構文エラーがないことを確認してください。

   使用して、**読み取り専用シンボル ディレクティブ**シンボルの定義のみを含むファイルをインクルードするボックスです。 リソース定義が含まれていない、ファイルを保存すると、それ以外の場合に重複するリソースの定義が作成されます。

1. 指定したファイルにシンボルを配置します。

   この方法でインクルード ファイル内のシンボルは、リソース ファイルを開くたびに評価されますが、ファイルを保存するときに、ディスク上に置き換えはありません。

1. **[OK]** を選択します。

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>リソースのシンボル用のヘッダー ファイルの名前を変更するには

1. [リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)を右クリックし、 *.rc*ファイル[リソース ファイルのインクルード](../windows/resource-includes-dialog-box.md)します。

1. **シンボル ヘッダー ファイル**ボックスに、インクルード ファイルの新しい名前を入力します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース識別子 (シンボル)](../windows/symbols-resource-identifiers.md)<br/>
[方法: シンボルの作成](../windows/creating-new-symbols.md)<br/>
[定義済みシンボル ID](../windows/predefined-symbol-ids.md)<br/>