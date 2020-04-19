---
title: /link (リンカーにオプションを渡す)
ms.date: 03/25/2019
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: 37743e855c933b6236b5e7a837db257f332a3037
ms.sourcegitcommit: bbaf65f8ed1af12828b38f8eacd24f934ac0e538
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2019
ms.locfileid: "67155774"
---
# <a name="link-pass-options-to-linker"></a>/link (リンカーにオプションを渡す)

1 つまたは複数のリンカー オプションをリンカーに渡します。

## <a name="syntax"></a>構文

> **/link** *linker-options*

## <a name="arguments"></a>引数

*リンカー オプション*<br/>
リンカー オプションまたはリンカーに渡されるオプション。

## <a name="remarks"></a>Remarks

**/Link**オプションとリンカー オプションは、ファイル名と CL オプションの後に表示する必要があります。 スペースは間で必要な **/link**およびリンカー オプション。 詳細については、次を参照してください。 [MSVC リンカー参照](linking.md)します。

## <a name="example"></a>例

このサンプルのコマンドラインのコンパイル*hello.cpp*既存のオブジェクト ファイルにリンクと*there.obj*します。追加渡しますし **/VERSION**リンカー コマンド。

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

IDE は、通常のコンパイルし、コードをリンクする個別のコマンドを送信します。 プロジェクトのプロパティ ページで、リンカー オプションを設定できます。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. 選択、**構成プロパティ** > **リンカー**フォルダー。

1. 1 つまたは複数のプロパティを変更します。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- このコンパイラ オプションをプログラムで変更することはできません。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
