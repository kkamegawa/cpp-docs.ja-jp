---
title: /MANIFEST (side-by-side アセンブリ マニフェストを作成する)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
ms.openlocfilehash: ea58b43accdd854665fad3b70d7aecbc9eaa0f9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492777"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (side-by-side アセンブリ マニフェストを作成する)

```
/MANIFEST[:{EMBED[,ID=#]|NO}]
```

## <a name="remarks"></a>Remarks

/MANIFEST は、リンカーが side-by-side マニフェストファイルを作成することを指定します。 マニフェストファイルの詳細については、「[マニフェストファイルリファレンス](/windows/win32/SbsCs/manifest-files-reference)」を参照してください。

既定値は、"/MANIFEST" です。

/MANIFEST:EMBED オプションは、リンカーが RT_MANIFEST 型のリソースとしてイメージにマニフェスト ファイルを埋め込む必要があることを指定します。 省略可能な `ID` パラメーターは、マニフェストで使用するリソース ID です。 実行可能ファイルの場合は値 1 を使用します。 DLL の場合は値 2 を使用して、プライベート依存関係を指定できるようにします。 `ID` パラメーターを指定しない場合、/DLL オプションが設定されている場合の既定値は 2、それ以外の場合の既定値は 1 になります。

Visual Studio 2008 以降、実行可能ファイルのマニフェストファイルには、ユーザーアカウント制御 (UAC) 情報を指定するセクションが含まれています。 /マニフェストを指定し、 [/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)も[/dll](dll-build-a-dll.md)も指定しない場合、uac レベルが*asInvoker*に設定されている既定の uac フラグメントがマニフェストに挿入されます。 UAC レベルの詳細については、「 [/MANIFESTUAC (uac 情報をマニフェストに埋め込む)](manifestuac-embeds-uac-information-in-manifest.md)」を参照してください。

UAC の既定の動作を変更するには、次のいずれかを行います。

- /MANIFESTUAC オプションを指定して、UAC レベルを所定の値に設定します。

- マニフェストに UAC フラグメントを生成しない場合は、/MANIFESTUAC:NO オプションを指定します。

/マニフェストを指定せずに、 [/manifestdependency](manifestdependency-specify-manifest-dependencies.md)コメントを指定すると、マニフェストファイルが作成されます。 /MANIFEST:NO を指定すると、マニフェスト ファイルは作成されません。

/MANIFEST を指定すると、マニフェスト ファイルの名前は出力ファイルの名前と同じになりますが、ファイル名に .manifest が追加されます。 たとえば、出力ファイルの名前が MyFile.exe の場合、マニフェスト ファイル名は MyFile.exe.manifest になります。  /Manifestfile:*name*を指定した場合、マニフェストの名前は [*名前*] に指定した名前になります。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]** ノードを展開します。

1. **[リンカー]** ノードを展開します。

1. **[マニフェストファイル]** プロパティページを選択します。

1. マニフェストの**生成**プロパティを変更します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
