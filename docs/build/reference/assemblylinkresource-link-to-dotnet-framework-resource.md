---
title: /ASSEMBLYLINKRESOURCE (.NET Framework リソースへのリンク)
ms.date: 11/04/2016
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
ms.openlocfilehash: fb707a2721ed40ee3ec37d01b2bbcfcc51f05c38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295163"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (.NET Framework リソースへのリンク)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
アセンブリからリンクする .NET Framework のリソース ファイル。

## <a name="remarks"></a>Remarks

/ASSEMBLYLINKRESOURCE オプションは、出力ファイルで .NET Framework リソースへのリンクを作成します出力ファイルでは、リソース ファイルが配置されていません。 [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)リソース ファイル、出力ファイルに埋め込みます。

リンクされたリソースでは、リンカーで作成したアセンブリでパブリックです。

/ASSEMBLYLINKRESOURCE では、コンパイルが含まれている必要があります[/clr](clr-common-language-runtime-compilation.md);[/LN](ln-create-msil-module.md)または[/NOASSEMBLY](noassembly-create-a-msil-module.md) /ASSEMBLYLINKRESOURCE で許可されていません。

場合*filename*作成例についてでの .NET Framework リソース ファイルは、 [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)または開発環境でアクセスできるメンバー間で、 **System.Resources**名前空間。 詳細については、次を参照してください。 [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager)します。 他のすべてのリソースを使用して、**それ以外**\*メソッド、 **System.Reflection.Assembly**実行時にリソースにアクセスするクラス。

*ファイル名*任意のファイル形式を指定できます。 たとえば、グローバル アセンブリ キャッシュにインストールされているし、アセンブリ内のマネージ コードからアクセスできるように、ネイティブの DLL が、アセンブリの一部を作成したい場合があります。

アセンブリの生成に影響するその他のリンカー オプションがあります。

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

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
