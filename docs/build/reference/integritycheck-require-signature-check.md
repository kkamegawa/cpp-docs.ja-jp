---
title: /INTEGRITYCHECK (シグネチャ確認が必要)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 1732c612501b66753635b272f94764975c555f75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492846"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (シグネチャ確認が必要)

読み込み時にバイナリ イメージのデジタル署名を確認する必要があることを指定します。

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Remarks

既定では、 **/INTEGRITYCHECK**はオフになっています。

**/INTEGRITYCHECK**オプションは、DLL ファイルまたは実行可能ファイルの PE ヘッダーに、Windows でイメージを読み込むためにデジタル署名を確認するためのメモリマネージャーのフラグを設定します。 このオプションは、特定の Windows 機能によって読み込まれるカーネルモードコードを実装する32ビットと64ビットの両方の Dll に対して設定する必要があり、Windows Vista、Windows 7、Windows 8、Windows Server 2008、および Windows Server 2012 のすべてのデバイスドライバーに推奨されます。 Windows Vista 以前の Windows は、このフラグを無視します。 詳細については、「[ポータブル実行可能 (PE) ファイルの強制整合性署名](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)」を参照してください。

### <a name="to-set-this-linker-option-in-visual-studio"></a>このリンカー オプションを Visual Studio で設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]** ノードを展開します。

1. **[リンカー]** ノードを展開します。

1. **[コマンドライン]** プロパティページを選択します。

1. **[追加オプション]** で`/INTEGRITYCHECK` 、 `/INTEGRITYCHECK:NO`またはを入力します。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
[ポータブル実行可能 (PE) ファイルの強制整合性署名](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[カーネルモードコード署名の要件](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[AppInit Dll とセキュアブート](/windows/win32/dlls/secure-boot-and-appinit-dlls)
