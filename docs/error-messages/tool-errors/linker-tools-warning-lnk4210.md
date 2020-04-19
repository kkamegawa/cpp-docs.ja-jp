---
title: リンカー ツールの警告 LNK4210
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 75376129ce0033c717a4da3074cee9de132d357d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395067"
---
# <a name="linker-tools-warning-lnk4210"></a>リンカー ツールの警告 LNK4210

> セクション*セクション*存在しますある場合がありますハンドルされていない静的初期化子、または終末記号。

## <a name="remarks"></a>Remarks

いくつかのコードは、静的初期化子、または終末記号に導入されていますが、アプリケーションの起動時に、VCRuntime ライブラリのスタートアップ コードまたはそれと同等 (これは、静的初期化子または終端文字を実行する必要があります) で実行されていません。 静的初期化子または終端文字を必要とするコードのいくつかの例を次に示します。

- コンス トラクター、デストラクター、または仮想関数テーブルにクラスのグローバル変数。

- グローバル変数が非コンパイル時定数を使用して初期化します。

この問題を解決するには、次のいずれかを試してください。

- 静的初期化子を含むすべてのコードを削除します。

- 使用しない[/NOENTRY](../../build/reference/noentry-no-entry-point.md)します。 /NOENTRY を削除した後、削除する必要がありますも[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)リンカーのコマンドライン。

- ビルド/MT を使用する場合、リンカー コマンドラインに libcmt.lib、libvcruntime.lib、libucrt.lib を追加します。 ビルドは、/MTd を使用している場合は、libcmtd.lib、vcruntimed.lib ですと libucrtd.lib を追加します。

- /Clr から移動する場合:/clr:pure に純粋なコンパイルの削除、 [/ENTRY](../../build/reference/entry-entry-point-symbol.md)リンカー コマンドラインのオプション。 これにより、CRT の初期化でき、アプリケーションの起動時に実行する静的初期化子。 **/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

[/GS](../../build/reference/gs-buffer-security-check.md)コンパイラ オプションで初期化が必要です、`__security_init_cookie`関数。 この初期化は既定で実行されている、VCRuntime ライブラリのスタートアップ コードで提供される`_DllMainCRTStartup`します。

- /ENTRY を使用して、プロジェクトをビルドし、/ENTRY が渡される関数以外の場合`_DllMainCRTStartup`、関数を呼び出す必要があります`_CRT_INIT`CRT を初期化します。 /GS を使用して、静的初期化子が必要です、または MFC または ATL コードのコンテキストで呼び出される DLL 場合、この呼び出しだけでは十分ではありません。 参照してください[Dll と Visual C ランタイム ライブラリの動作](../../build/run-time-library-behavior.md)詳細についてはします。

## <a name="see-also"></a>関連項目

- [リンカー オプションの設定](../../build/reference/linking.md)
