---
title: /NOLOGO (著作権情報の非表示) (リンカー)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
ms.openlocfilehash: 0ef0c6f8e0073e7450daa8d0433ce4d6e82ceab8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320527"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (著作権情報の非表示) (リンカー)

```
/NOLOGO
```

## <a name="remarks"></a>Remarks

/NOLOGO オプションでは、著作権のメッセージとバージョン番号が表示されなくなります。

このオプションはまた、コマンド ファイルのエコーを抑制します。 詳細については、次を参照してください。 [LINK コマンド ファイル](linking.md)します。

既定では、この情報は、出力ウィンドウに、リンカーによって送信されます。 コマンドラインでは、標準出力に送信され、ファイルにリダイレクトできます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. このオプションは、コマンドラインからのみ使用する必要があります。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. このリンカー オプションをプログラムで変更することはできません。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
