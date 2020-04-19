---
title: /EXPORT (関数のエクスポート)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: 7c4f4621bbccd4285bcf4eca07d2544d53d14f6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271360"
---
# <a name="export-exports-a-function"></a>/EXPORT (関数のエクスポート)

プログラムから名前または序数、または、データでの関数をエクスポートします。

## <a name="syntax"></a>構文

> **/EXPORT:**<em>entryname</em>[**,\@**<em>ordinal</em>**[,NONAME]** **[,DATA]**

## <a name="remarks"></a>Remarks

**/Export**オプションが他のプログラムを関数を呼び出すか、データを使用するために、プログラムからエクスポートする関数またはデータ項目を指定します。 エクスポートは、通常は DLL で定義されます。

*Entryname*関数またはデータ項目の名前は、呼び出し元プログラムで使用されます。 *序数に基づく*を指定しない場合は、1 ~ 65,535; の範囲内のエクスポート テーブルにインデックスを指定します*序数*、いずれかのリンクが割り当てられます。 **NONAME**キーワード関数をエクスポート序数としてのみせず、 *entryname*します。

**データ**キーワードは、エクスポートされた項目がデータ項目を指定します。 使用して、クライアント プログラム内のデータ項目を宣言する必要があります**extern _declspec**します。

使用の推奨される順序で、定義をエクスポートするための 4 つの方法はあります。

1. [方式](../../cpp/dllexport-dllimport.md)でソース コード

1. [エクスポート](exports.md).def ファイル内のステートメント

1. LINK コマンドで、/EXPORT 仕様

1. A[コメント](../../preprocessor/comment-c-cpp.md)形式のソース コードにディレクティブ`#pragma comment(linker, "/export: definition ")`します。

これらすべてのメソッドは、同じプログラム内で使用できます。 リンクは、エクスポートを含むプログラムをビルドも作成、インポート ライブラリのビルドで .exp ファイルを使用しない場合。

リンクは、装飾された識別子の形式。 コンパイラは、.obj ファイルの作成時に識別子を修飾します。 場合*entryname*その非装飾にはリンカーに指定された形式 (ソース コードに表示されます)、リンクは、名前を照合しようとしています。 一意の一致が見つからない場合、リンクは、エラー メッセージを発行します。 使用して、 [DUMPBIN](dumpbin-reference.md)を取得するためのツール、[装飾名](decorated-names.md)リンカーに指定する必要がある場合は、識別子の形式。

> [!NOTE]
> 宣言されている C 識別子の装飾形式を指定しない`__cdecl`または`__stdcall`します。

非装飾関数名をエクスポートし、ビルド構成に応じてさまざまなエクスポートが (たとえば、32 ビットまたは 64 ビットのビルド) である必要がある場合は、各構成の別の DEF ファイルを使用できます。 (プリプロセッサの条件付きディレクティブは使用できません DEF ファイルにします。)代わりに、使用することができます、`#pragma comment`関数宣言の前にディレクティブここで、`PlainFuncName`非装飾の名前と`_PlainFuncName@4`関数の装飾の名前を指定します。

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. オプションを入力して、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
