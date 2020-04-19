---
title: リソース ファイル (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: b66a207766962856cc4d7181607868c2a48ebe84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513660"
---
# <a name="resource-files-c"></a>リソース ファイル (C++)

> [!NOTE]
> .NET プログラミング言語のプロジェクトでは、リソース スクリプト ファイルは使用しないため、 **ソリューション エクスプローラー**」をご覧ください。 [イメージエディター](../windows/image-editor-for-icons.md)と[バイナリエディター](binary-editor.md)を使用して、マネージプロジェクトのリソースファイルを操作します。
>
> 編集の対象となるマネージド リソースは、リンク リソースである必要があります。 Visual Studio のリソース エディターでは、埋め込みリソースの編集はサポートしていません。

*リソースファイル*という用語は、次のようなさまざまな種類のファイルを参照できます。

- プログラムのリソース スクリプト (.rc) ファイル。

- リソース テンプレート (.rct) ファイル。

- スタンドアロンファイルとして存在する個々のリソース。 この型には、.rc ファイルから参照されるビットマップ、アイコン、またはカーソルファイルが含まれています。

- 開発環境によって生成されるヘッダーファイル。 この型に`Resource.h`は、.rc ファイルから参照されているが含まれます。

.Exe、.dll、.res ファイルなど、他のファイルの種類で見つかったリソースは、*リソース*と呼ばれます。

*リソースファイル*とリソースは、プロジェクト内から操作できます。 また、現在のプロジェクトの一部ではないものや、Visual Studio の開発環境の外部で作成されたものを使用することもできます。 たとえば、次のように操作できます。

- 入れ子になっていて、条件付きでインクルードされるリソース ファイルの操作。

- 既存のリソースを更新するか、 C++ビジュアルに変換します。

- グラフィック リソースを現在のリソース ファイルとの間でインポートまたはエクスポートする。

- 開発環境では変更できない共有または読み取り専用識別子 (シンボル) のインクルード。

- 複数のプロジェクト間で共有されるリソースなど、編集を必要としない (または編集しない) 実行可能 (.exe) ファイルにリソースを含めます。

- 開発環境でサポートされていない種類のリソースのインクルード。

リソースの詳細については、「[コンパイル時に](../windows/how-to-include-resources-at-compile-time.md)[リソースを作成](../windows/how-to-create-a-resource-script-file.md)し、リソースを[管理](../windows/how-to-copy-resources.md)し、リソースを含める方法」を参照してください。

## <a name="editable-resources"></a>編集可能なリソース

次の種類のファイルを開いて、含まれているリソースを編集できます。

| ファイル名 | 説明 |
|---|---|
| .rc | リソーススクリプトファイル |
| .rct | リソーステンプレートファイル |
| .res | リソース ファイル |
| .resx | マネージリソースファイル |
| .exe | 実行可能ファイル |
| .dll | ダイナミックリンクライブラリファイル |
| .bmp、.ico、.dib、. 同一 | ビットマップ、アイコン、ツールバー、およびカーソルファイル |

リソースを編集する場合、Visual Studio 環境はと連携し、次のファイルに影響します。

| ファイル名 | 説明 |
|---|---|
| Resource.h | シンボル定義を含む開発環境によって生成されるヘッダーファイル。<br/><br/>このファイルをソース管理に含めます。 |
| Filename.aps | クイック読み込みに使用される現在のリソーススクリプトファイルのバイナリバージョン。<br /><br /> リソースエディターは、.rc ファイルまたは resource.h ファイルを直接読み取りません。 リソースコンパイラは、リソースエディターによって使用される aps ファイルにそれらをコンパイルします。 これはコンパイル手順のファイルで、シンボル データのみが格納されます。<br/><br/>通常のコンパイルプロセスと同様に、コメントなどのシンボルではない情報は、コンパイルプロセス中に破棄されます。<br/><br/>ファイルが .rc ファイルと同期されていない場合は常に、.rc ファイルが再生成されます。 たとえば、を**保存**すると、リソースエディターによって .rc ファイルと resource.h ファイルが上書きされます。 リソース自体に対する変更は、.rc ファイルに組み込まれたままになりますが、.rc ファイルが上書きされると、コメントは常に失われます。 コメントを保持する方法の詳細については、「[コンパイル時にリソースを含める](../windows/how-to-include-resources-at-compile-time.md)」を参照してください。<br/><br/>通常、ソース管理には、aps ファイルを含めないでください。 |
| .rc | 現在のプロジェクト内のリソース用のスクリプトを格納するリソース スクリプト ファイル。 このファイルは、保存するたびに .aps ファイルで上書きされます。<br/><br/>このファイルをソース管理に含めます。 |

## <a name="manifest-resources"></a>マニフェスト リソース

デスクトップC++プロジェクトでは、マニフェストリソースは、アプリケーションが使用する依存関係を記述する XML ファイルです。 たとえば、Visual Studio では、この MFC ウィザードで生成されたマニフェストファイルで、アプリケーションで使用する Windows コモンコントロール Dll のバージョンを定義します。

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Windows XP または Windows Vista アプリケーションの場合、マニフェストリソースは、アプリケーションで使用する Windows コモンコントロールの最新バージョンを指定する必要があります。 上記の例では`6.0.0.0`、 [syslink コントロール](/windows/win32/Controls/syslink-overview)をサポートするバージョンが使用されています。

> [!NOTE]
> 使用できるマニフェスト リソースは 1 つのモジュールにつき 1 つだけです。

マニフェストリソースに含まれるバージョン情報と型情報を表示するには、XML ビューアーまたは Visual Studio テキストエディターでファイルを開きます。 マニフェスト リソースを [リソース ビュー](../windows/resource-view-window.md)から開くと、リソースはバイナリ形式で表示されます。

### <a name="to-open-a-manifest-resource"></a>マニフェストリソースを開くには

1. Visual Studio でプロジェクトを開き、**ソリューションエクスプローラー**に移動します。

1. **[リソースファイル]** フォルダーを展開し、次のように入力します。

   - テキストエディターでを開くには、 *.manifest*ファイルをダブルクリックします。

   - 別のエディターで開くには、 *.manifest*ファイルを右クリックし、[ファイル**を開くアプリケーション**の選択] をクリックします。 使用するエディターを指定し、 **[開く]** を選択します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース ファイルの操作](../windows/working-with-resource-files.md)<br/>
[リソース識別子 (シンボル)](../windows/symbols-resource-identifiers.md)<br/>
[リソース エディター](../windows/resource-editors.md)<br/>