---
title: /KEYFILE (アセンブリに署名するためのキーまたはキー ペアの指定)
ms.date: 11/04/2016
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
ms.openlocfilehash: d309390c1ac1a19d9d4a982908dbbbac0bd52714
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291562"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (アセンブリに署名するためのキーまたはキー ペアの指定)

```
/KEYFILE:filename
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
キーを含むファイルです。 二重引用符で区切る文字列を配置 ("")、スペースが含まれている場合。

## <a name="remarks"></a>Remarks

リンカーはアセンブリ マニフェストに公開キーを挿入し、秘密キーで最終アセンブリに署名します。 キー ファイルを生成する入力[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*コマンドライン。 署名されたアセンブリは、厳密な名前と呼ばれます。

使用してコンパイルする場合[/LN](ln-create-msil-module.md)、キー ファイルの名前がモジュールに保持されを使用して、モジュールを明示的に参照を含むアセンブリをコンパイルするときに作成されるアセンブリに組み込む[#using](../../preprocessor/hash-using-directive-cpp.md)とをリンクするときまたは[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)します。

リンカーに、暗号化情報を渡すことができますも[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)します。 使用[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)部分的に署名されたアセンブリを作成する場合。 参照してください[厳密な名前のアセンブリ (アセンブリ署名) (C +/cli CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)アセンブリへの署名の詳細についてはします。

場合両方 **/KEYFILE**と **/KEYCONTAINER**が指定されて、リンカーは、キー コンテナーをまず (コマンド ライン オプションまたはカスタム属性によって)、します。 それが成功すると、アセンブリはキー コンテナーの情報で署名されます。 リンカーがキー コンテナーを見つけられない場合/KEYFILE で指定されたファイルが試みられます。 ファイルが検出された場合、アセンブリはキー ファイルの情報で署名され、キー情報はキー コンテナーにインストールされるため (sn -i と同様)、次のコンパイル時にはキー コンテナーが有効になります。

キー ファイルには公開キーだけが含まれる場合があることに注意してください。

参照してください[の作成と using strong-named Assemblies](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)アセンブリへの署名の詳細についてはします。

アセンブリの生成に影響するその他のリンカー オプションがあります。

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. オプションを入力、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
