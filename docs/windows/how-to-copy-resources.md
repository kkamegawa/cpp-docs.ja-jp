---
title: '方法: リソースの管理C++()'
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 718de310bc4fb0cb0072065bc4e7b7adadb182aa
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740662"
---
# <a name="how-to-manage-resources-c"></a>方法: リソースの管理C++()

## <a name="copy-and-edit-resources"></a>リソースのコピーと編集

ファイルを変更することなく、あるファイルから別のファイルにリソースをコピーしたり、リソースのコピー中にリソースの言語や条件を変更したりできます。

既存のリソースまたは実行可能ファイルから現在のリソースファイルにリソースを簡単にコピーできます。 リソースをコピーするには、リソースが含まれている両方のファイルを同時に開き、1つのファイルから別のファイルに項目をドラッグします。2つのファイルをコピーして貼り付けることもできます。 このメソッドは、リソーススクリプト (.rc) ファイルとリソーステンプレート (.rct) ファイル、および実行可能 (.exe) ファイルとして機能します。

> [!NOTE]
> ビジュアルC++には、独自のアプリケーションで使用できるサンプルリソースファイルが含まれています。 詳細については[、「クリップアート:共通リソース](https://github.com/Microsoft/VCSamples)。

プロジェクト (**リソースビュー**) 内のリソースファイルと、ドキュメントウィンドウでスタンドアロンの .rc ファイルの間でドラッグアンドドロップ、コピー、切り取り、貼り付けを行うことはできません。 これは、以前のバージョンの製品で行うことができます。 プロジェクトの外部で開かれている .rc ファイル間でドラッグアンドドロップのメソッドのみを使用します。

### <a name="to-copy-resources"></a>リソースをコピーするには

1. 2 つのリソース ファイルをスタンドアロンで開きます。 (「[リソーススクリプトファイルの使用」を](how-to-create-a-resource-script-file.md#use-resource-script-files)参照してください)。 たとえば、 *Source1*と*Source2*を開きます。

1. 最初の .rc ファイル内で、次のいずれかの方法を実行します。

   - ドラッグアンドドロップの方法を使用する

      1. コピーするリソースを選択します。 たとえば、 *Source1*で、 **[IDD_DIALOG1]** を選択します。

      1. **Ctrl**キーを押しながら、リソースを2番目の .rc ファイルにドラッグします。 たとえば、 **IDD_DIALOG1**を*Source1*から*Source2*にドラッグします。

         > [!TIP]
         > **Ctrl**キーを押したままリソースをドラッグしても、リソースはコピーされずに移動します。

   - コピーと貼り付けの方法を使用する

      1. コピーするリソース (たとえば、 *Source1*) を右クリックし、 **[コピー]** を選択します。

      1. リソースを貼り付けるリソースファイル (たとえば、 *Source2*) を右クリックし、 **[貼り付け]** を選択します。

> [!NOTE]
> 既存のファイルのシンボル名または値との競合を避けるC++ために、新しいファイルにコピーするときに、移動されたリソースのシンボル値またはシンボル名と値がビジュアルによって変更されることがあります。

リソースのコピー時に、リソースの言語プロパティ、条件プロパティ、またはその両方を変更できます。

- リソースの言語では、検索対象のリソースを識別するために[Findresource](/windows/win32/api/winbase/nf-winbase-findresourcea)によって使用される言語を指定します。 リソースには、テキストに関連付けられていない言語ごとに異なるものを含めることができます。たとえば、日本語キーボードでのみ動作するアクセラレータや、中国語のローカライズされたビルドにのみ適したビットマップなどです。

- リソースの条件とは、リソースの特定のコピーが使用される条件を識別する定義済みのシンボルです。

リソースの言語と条件は、**ワークスペース**ウィンドウのリソース名の後にかっこで囲まれて表示されます。 ここで、と`IDD_AboutBox`いう名前`Finnish`のリソースは言語として`XX33`を使用し、その条件は次のようになります。

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>既存のリソースをコピーして、そのリソースの言語または条件を変更するには

*.Rc*ファイルまたは [[リソースビュー](how-to-create-a-resource-script-file.md#create-resources) ] ウィンドウで、コピーするリソースを右クリックし、 **[コピーの挿入]** を選択します。 次のように設定します。

- **[言語]** ボックスの一覧で、言語を選択します。

- **[条件]** ボックスに、条件を入力します。

### <a name="to-edit-resources"></a>リソースを編集するには

マネージリソース (.resx) ファイルは XML ファイルです。 **[新しい項目の追加]** ダイアログボックスからマネージリソースファイルをプロジェクトに追加すると、 **[マネージリソースエディター]** が既定で開きます。

## <a name="import-and-export-resources"></a>リソースのインポートとエクスポート

グラフィカル リソース (ビットマップ、アイコン、カーソル、ツール バー)、HTML ファイル、および Visual C++ で使用するためのカスタム リソースをインポートすることができます。 Visual Studio C++プロジェクトから同じ種類のファイルをエクスポートして、開発環境の外部で使用できるファイルを分離することができます。

> [!NOTE]
> アクセラレータ、ダイアログボックス、文字列テーブルなどのリソースの種類は、スタンドアロンのファイルの種類ではないため、インポートまたはエクスポートできません。

### <a name="to-import-a-resource-into-the-resource-script-file"></a>リソースをリソーススクリプトファイルにインポートするには

1. で、リソースを追加するリソーススクリプト (.rc) ファイルのノードを右クリックし、 **[インポート]** を選択し[リソースビュー](how-to-create-a-resource-script-file.md#create-resources)ます。

1. ビットマップ (.bmp)、アイコン (.ico)、カーソル (...)、html ファイル (.htm)、またはその他のインポートするファイルの名前を探して選択します。

1. [ **OK]** を選択して、リソースをリソーススクリプトファイルに追加します。

> [!NOTE]
> インポートプロセスは、選択したリソースの種類に関係なく同じように動作します。 インポートされたリソースは、そのリソースの種類の適切なノードに自動的に追加されます。

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>ビジュアルの外部で使用するためにリソースをエクスポートするにはC++

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)で、エクスポートするリソースを右クリックし、 **[エクスポート]** を選択します。 現在のファイル名をそのまま使用することも、新しいファイル名を入力することもできます。

1. ファイルを保存するフォルダーに移動し、 **[エクスポート]** を選択します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース ファイル](../windows/resource-files-visual-studio.md)<br/>
[方法: リソースの作成](../windows/how-to-create-a-resource-script-file.md)<br/>
[方法: コンパイル時にリソースをインクルードする](../windows/how-to-include-resources-at-compile-time.md)<br/>