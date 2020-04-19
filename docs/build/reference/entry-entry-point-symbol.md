---
title: /ENTRY (エントリ ポイント シンボル)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 0f3604ef75ce10928463c088e423615886555eda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293213"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (エントリ ポイント シンボル)

```
/ENTRY:function
```

## <a name="arguments"></a>引数

*function*<br/>
ユーザーが定義した開始を指定する関数は、.exe ファイルまたは DLL のアドレスします。

## <a name="remarks"></a>Remarks

/ENTRY オプションは、.exe ファイルまたは DLL の開始アドレスとしてエントリ ポイント関数を指定します。

使用する関数を定義する必要があります、`__stdcall`呼び出し規約。 パラメーターと戻り値のかどうか、プログラムはコンソール アプリケーション、windows アプリケーションまたは DLL に依存します。 エントリ ポイントを設定して、C ランタイム ライブラリが正しく初期化され、静的オブジェクトに対して C++ コンス トラクターが実行されるようにリンカーを使用することをお勧めします。

既定では、開始アドレスは、C ランタイム ライブラリから関数名です。 リンカーは、プログラムの属性に基づいて次の表に示すように、ように選択します。

|関数名|既定値|
|-------------------|-----------------|
|**mainCRTStartup** (または**wmainCRTStartup**)|/SUBSYSTEM:CONSOLE; を使用するアプリケーション呼び出し`main`(または`wmain`)|
|**WinMainCRTStartup** (または**wWinMainCRTStartup**)|/SUBSYSTEM を使用するアプリケーション:**WINDOWS**; 呼び出し`WinMain`(または`wWinMain`) を使用して定義されている必要があります `__stdcall`|
|**_DllMainCRTStartup**|DLL。呼び出し`DllMain`する必要がありますを使用する定義が存在する場合 `__stdcall`|

場合、 [/DLL](dll-build-a-dll.md)または[/SUBSYSTEM](subsystem-specify-subsystem.md)をリンカーがかどうかに応じてサブシステムとエントリ ポイントを選択して、オプションが指定されていない`main`または`WinMain`が定義されています。

関数は、 `main`、 `WinMain`、および`DllMain`ユーザー定義のエントリ ポイントの 3 つの形式します。

管理対象イメージを作成するには、/ENTRY に指定された関数での署名が必要 (LPVOID *var1*、DWORD *var2*、LPVOID *var3*)。

独自に定義する方法については`DllMain`、エントリ ポイントを参照してください[Dll と Visual C ランタイム ライブラリの動作](../run-time-library-behavior.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**詳細**プロパティ ページ。

1. 変更、**エントリ ポイント**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
