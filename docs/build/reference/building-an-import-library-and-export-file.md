---
title: インポート ライブラリとエクスポート ファイルのビルド
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
ms.openlocfilehash: 37c3169b66e1120dbfdb3a69379430e9bc8a1586
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294791"
---
# <a name="building-an-import-library-and-export-file"></a>インポート ライブラリとエクスポート ファイルのビルド

ファイルのエクスポートをインポート ライブラリをビルドし、するには、次の構文を使用します。

> **LIB /DEF**[**:**<em>deffile</em>] [*options*] [*objfiles*] [*libraries*]

/DEF を指定すると、LIB は LIB コマンドに渡されるエクスポート定義からの出力ファイルを作成します。 使用の推奨される順序で、エクスポートを指定するための 3 つの方法はあります。

1. A**方式**のいずれかで定義、 *objfiles*または*ライブラリ*

1. /EXPORT の指定:*名前*LIB コマンドラインで

1. 定義、**エクスポート**内のステートメントを*deffile*

これらは、エクスポートするプログラムをリンクするときに、エクスポートを指定するときと同じ方法です。 プログラムでは、1 つ以上のメソッドを使用できます。 LIB のコマンドは、の部分を指定することができます (複数など*objfiles*または/EXPORT の仕様) LIB コマンドでコマンド ファイルでだけできる限り LINK コマンドでします。

次のオプションは、インポート ライブラリをビルドに適用され、ファイルのエクスポートします。

> **/OUT:** *import*

既定の出力ファイル名をオーバーライド、*インポート*ライブラリを作成します。 既定の名前は、最初のオブジェクト ファイルまたは LIB コマンドと、拡張機能ライブラリのベース名で/OUT が指定されていない場合。 lib します。 エクスポート ファイルがインポート ライブラリと拡張機能として同じ基本名を指定します。 exp します。

> **/EXPORT:** *entryname*\[**=** *internalname*]\[,**\@**<em>ordinal</em>\[, **NONAME**]]\[, **DATA**]

関数を呼び出すには、他のプログラムを許可するプログラムから関数をエクスポートします。 データをエクスポートすることもできます (を使用して、**データ**キーワード)。 エクスポートは、通常は DLL で定義されます。

*Entryname*関数またはデータ項目の名前は、呼び出し元プログラムで使用されます。 必要に応じて、指定、 *internalname*既知の定義のプログラムでは、既定では、関数として*internalname*と同じ*entryname*します。 *序数*を指定しない場合は、1 ~ 65,535; の範囲内のエクスポート テーブルにインデックスを指定します*序数*LIB は 1 つ割り当てられます。 **NONAME**キーワード関数をエクスポート序数としてのみせず、 *entryname*します。 **データ**オブジェクトのデータのみをエクスポートするキーワードを使用します。

> **/INCLUDE:** *シンボル*

指定した追加*シンボル*シンボル テーブルにします。 このオプションは、それ以外の場合は対象外とするライブラリ オブジェクトの使用を強制する場合に便利です。

.Dll を作成する前に、準備手順で、インポート ライブラリを作成する場合を渡す必要がある同じ一連のオブジェクト ファイル、.dll を作成するときにインポート ライブラリを構築するときに渡されたことに注意してください。

## <a name="see-also"></a>関連項目

[インポート ライブラリとエクスポート ファイル](working-with-import-libraries-and-export-files.md)
