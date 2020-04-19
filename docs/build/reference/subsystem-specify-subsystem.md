---
title: /SUBSYSTEM (サブシステムの指定)
ms.date: 11/04/2016
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
ms.openlocfilehash: ecda3443d0422af4d5ceec9282d86590c53af2f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318246"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (サブシステムの指定)

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|
            POSIX|WINDOWS)
            [,major[.minor]]
```

## <a name="arguments"></a>引数

**BOOT_APPLICATION**<br/>
Windows のブート環境で実行するアプリケーションです。 ブート アプリケーションの詳細については、次を参照してください。 [About BCD](/previous-versions/windows/desktop/bcd/about-bcd)します。

**コンソール**<br/>
Win32 文字モード アプリケーションに対して使用します。 オペレーティング システムには、コンソール アプリケーションのコンソールが用意されています。 ネイティブ コードに `main` または `wmain` が定義されている場合、マネージド コードに `int main(array<String ^> ^)` が定義されている場合、または `/clr:safe` を使用してアプリケーションを完全にビルドする場合、CONSOLE が既定の設定になります。

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Extensible Firmware Interface サブシステムです。 詳細については、EFI の仕様を参照してください。 例については、Intel の Web サイトを参照してください。 最小および既定のバージョンは 1.0 です。

**ネイティブ**<br/>
Windows NT 用のカーネル モード ドライバーです。 このオプションは、通常、Windows システム コンポーネントのために予約されています。 場合[/DRIVER:WDM](driver-windows-nt-kernel-mode-driver.md)を指定すると、既定では、ネイティブです。

**POSIX**<br/>
Windows NT 上の POSIX サブシステムで実行するアプリケーションです。

**WINDOWS**<br/>
アプリケーションにはコンソールは不要です。このシステムにはユーザーとの対話用のウィンドウが作成されるからです。 ネイティブ コードに `WinMain` または `wWinMain` が定義されている場合、あるいはマネージド コードに `WinMain(HISTANCE *, HINSTANCE *, char *, int)` または `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` が定義されている場合、WINDOWS が既定の設定になります。

*主要な*と*マイナー*<br/>
(省略可能)サブシステムの最低限必要なバージョンを指定します。 引数には、0 ～ 65535 の範囲の 10 進数を指定します。 詳細については、「解説」を参照してください。 バージョン番号に上限はありません。

## <a name="remarks"></a>Remarks

**/SUBSYSTEM**オプションは、実行可能ファイルの環境を指定します。

サブシステムの選択によって、リンカーが選択するエントリ ポイント シンボル (またはエントリ ポイント関数) が決まります。

省略可能な最小値と既定*メジャー*と*マイナー*サブシステムのバージョン番号は、次のとおりです。

|サブシステム|最小要件|既定値|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1|1|
|CONSOLE|(x86) 5.01 (x64) 5.02 6.02 です (ARM)|(x86、x64) は 6.00 6.02 です (ARM)|
|WINDOWS|(x86) 5.01 (x64) 5.02 6.02 です (ARM)|(x86、x64) は 6.00 6.02 です (ARM)|
|NATIVE (DRIVER:WDM を使用する場合)|(x86) 1.00 1.10 (x64、ARM)|(x86) 1.00 1.10 (x64、ARM)|
|NATIVE (/DRIVER:WDM を使用しない場合)|(x86) 4.00 (x64) 5.02 6.02 です (ARM)|(x86) 4.00 (x64) 5.02 6.02 です (ARM)|
|POSIX|1|19.90|
|EFI_APPLICATION、EFI_BOOT_SERVICE_DRIVER、EFI_ROM、EFI_RUNTIME_DRIVER|1|1|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. [リンカー] フォルダーを選択します。

1. 選択、**システム**プロパティ ページ。

1. `SubSystem` プロパティを変更します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
