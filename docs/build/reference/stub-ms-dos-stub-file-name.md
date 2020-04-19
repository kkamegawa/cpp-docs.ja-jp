---
title: /STUB (MS-DOS スタブ ファイル名)
ms.date: 11/04/2016
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
ms.openlocfilehash: 7150d4ff8f35b00d96caa21fd5ea3754fec76030
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317875"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (MS-DOS スタブ ファイル名)

```
/STUB:filename
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
MS-DOS アプリケーション。

## <a name="remarks"></a>Remarks

/STUB オプションは、MS-DOS スタブ プログラムを Win32 プログラムにアタッチします。

Ms-dos では、ファイルが実行される場合は、スタブ プログラムが呼び出されます。 通常、適切なメッセージが表示されます。ただし、任意の有効な MS-DOS アプリケーションは、スタブ プログラムを指定できます。

指定、 *filename*コマンドラインでは、コロン (:) の後にスタブ プログラム。 リンカー チェック*filename*し、ファイルが実行可能ファイルではない場合、エラー メッセージを発行します。 プログラムは、.exe ファイルである必要があります。スタブ プログラム .com ファイルが正しくありません。

このオプションを使用しない場合、リンカーには、次のメッセージを発行する既定のスタブ プログラムがアタッチされます。

```
This program cannot be run in MS-DOS mode.
```

仮想デバイス ドライバーを作成するときに*filename* (WINNT で定義されている IMAGE_DOS_HEADER 構造体を含むファイル名を指定できます。H) をクリックし、既定のヘッダーではなく、VXD で使用します。

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
