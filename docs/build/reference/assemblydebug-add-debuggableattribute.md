---
title: /ASSEMBLYDEBUG (DebuggableAttribute の追加)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: b9899ea76b7a23a0d09442fca01e7d968c5e8aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273093"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (DebuggableAttribute の追加)

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ASSEMBLYDEBUG 出力、 **DebuggableAttribute**デバッグ情報の追跡と無効にします。 JIT の最適化を持つ属性です。 これは、ソースで、次の属性を指定すると同じです。

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

/ASSEMBLYDEBUG:DISABLE 出力、 **DebuggableAttribute**属性がデバッグ情報の追跡を無効にし、JIT の最適化を有効します。 これは、ソースで、次の属性を指定すると同じです。

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

既定では出力されません、 **DebuggableAttribute**属性。

DebuggableAttribute は、ソース コードで直接アセンブリにも追加できます。 例えば以下のようにします。

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>Remarks

管理対象イメージがデバッグ可能であることを明示的に指定する必要があります。 使用して[/Zi](z7-zi-zi-debug-information-format.md)単独では不十分です。

アセンブリの生成に影響するその他のリンカー オプションがあります。

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**デバッグ**プロパティ ページ。

1. 変更、**デバッグできるアセンブリ**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
