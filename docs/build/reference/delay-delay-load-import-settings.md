---
title: /DELAY (遅延読み込みのインポート設定)
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493008"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (遅延読み込みのインポート設定)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Remarks

/DELAY オプションは、Dll の[遅延読み込み](linker-support-for-delay-loaded-dlls.md)を制御します。

- UNLOAD 修飾子は、DLL の明示的なアンロードをサポートするように遅延読み込みヘルパー関数に指定します。 インポート アドレス テーブル (IAT) は元の形式にリセットされ、IAT のポインターは無効になって上書きされます。

   [アンロード] を選択しない場合、 [FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md)の呼び出しは失敗します。

- NOBIND 修飾子は、バインドできる IAT を最終イメージに含めないようにリンカーに指定します。 既定では、遅延読み込みされる DLL に対してバインドできる IAT が作成されます。 生成されるイメージは静的にバインドできません。 (バインドできる IAT を含むイメージは、実行前に静的にバインドできます)。「 [/BIND](bind.md)」を参照してください。

   DLL がバインドされている場合、ヘルパー関数は、参照される各インポートで[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)を呼び出す代わりに、バインドされた情報を使用しようとします。 タイムスタンプまたは優先アドレスが、読み込まれた DLL のものと一致しない場合、ヘルパー関数はバインドされた IAT は古いと見なし、バインドされた IAT が存在しないかのように続行します。

   NOBIND を使用すると、プログラム イメージは大きくなりますが、DLL の読み込み時間は速くなります。 DLL をバインドしない場合は、NOBIND を使用すると、バインドされた IAT は生成されません。

遅延読み込みを行う Dll を指定するには、 [/DELAYLOAD](delayload-delay-load-import.md)オプションを使用します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「 [Visual Studio でのC++コンパイラとビルドプロパティの設定](../working-with-project-properties.md)」を参照してください。

1. **[構成プロパティ]** 、 **[リンカー]** の順に展開し、 **[詳細設定]** を選択します。

1. **遅延読み込み DLL**プロパティを変更します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
