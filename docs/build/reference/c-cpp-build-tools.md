---
title: その他の MSVC ビルドツール
ms.date: 08/28/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 53c7c2f8c162cd851b4612e75ba14b019d9cbd63
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177298"
---
# <a name="additional-msvc-build-tools"></a>その他の MSVC ビルドツール

Visual Studio には、ビルド出力を表示または操作するための次のコマンドラインユーティリティが用意されています。

- [LIB。EXE](lib-reference.md)は、COFF (Common Object File Format) オブジェクトファイルのライブラリを作成および管理するために使用されます。 エクスポートファイルを作成し、エクスポートされた定義を参照するためにライブラリをインポートするために使用することもできます。

- [EDITBIN。EXE](editbin-reference.md)は、COFF バイナリファイルを変更するために使用されます。

- [DUMPBIN。EXE](dumpbin-reference.md) COFF バイナリファイルに関する情報 (シンボルテーブルなど) を表示します。

- [NMAKE](nmake-reference.md)は makefile を読み取り、実行します。

- エラー参照ユーティリティ[ERRLOOK](value-edit-control.md)は、入力された値に基づいてシステムエラーメッセージまたはモジュールエラーメッセージを取得します。

- [XDCMake](xdcmake-reference.md)。 XML タグでマークされたドキュメントコメントを含むソースコードファイルを処理するためのツール。

- [BSCMAKE。EXE](bscmake-reference.md) (旧バージョンとの互換性のためにのみ提供) は、プログラム内のシンボル (クラス、関数、データ、マクロ、および型) に関する情報を含むブラウザー情報ファイル (.bsc) をビルドします。 この情報は、開発環境内の [参照] ウィンドウで表示します。 (.Bsc ファイルは、開発環境でもビルドできます)。

Windows SDK には、RC を含むいくつかのビルドツールもあり[ます。EXE](/windows/win32/menurc/resource-compiler)。ダイアログ、 C++プロパティページ、ビットマップ、文字列テーブルなど、ネイティブの Windows リソースをコンパイルするためにコンパイラによって呼び出されます。

## <a name="see-also"></a>関連項目

[C/C++ ビルドのリファレンス](c-cpp-building-reference.md)<br/>
[装飾名](decorated-names.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC リンカー オプション](linker-options.md)
