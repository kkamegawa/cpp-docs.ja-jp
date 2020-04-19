---
title: LIB の概要
description: ライブラリツール (lib) の使用方法とオプションの概要について説明します。
ms.date: 02/09/2020
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 5829a65ab0dc4ef193236c9ae480856a17c5874c
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257613"
---
# <a name="overview-of-lib"></a>LIB の概要

LIB (lib) は、プログラムをビルドするときに、[リンク](linker-options.md)で使用できる標準ライブラリ、インポートライブラリ、およびエクスポートファイルを作成します。 LIB は、コマンドプロンプトから実行します。

LIB は、次のモードで使用できます。

- [COFF ライブラリのビルドまたは変更](managing-a-library.md)

- [ファイルへのメンバーオブジェクトの抽出](extracting-a-library-member.md)

- [エクスポートファイルとインポートライブラリを作成する](working-with-import-libraries-and-export-files.md)

これらのモードは相互に排他的です。LIB は一度に1つのモードでのみ使用できます。

## <a name="lib-options"></a>LIB オプション

次の表に、lib のオプションと詳細情報へのリンクを示します。

|オプション|説明|
|-|-|
|**/DEF**|インポートライブラリとエクスポートファイルを作成します。<br/><br/>詳細については、「[インポートライブラリとエクスポートファイルのビルド](building-an-import-library-and-export-file.md)」を参照してください。|
|**/ERRORREPORT**| 非推奨。 詳細については、「[LIB の実行](running-lib.md)」を参照してください。|
|**/EXPORT**|   関数をプログラムからエクスポートします。<br/><br/>詳細については、「[インポートライブラリとエクスポートファイルのビルド](building-an-import-library-and-export-file.md)」を参照してください。|
|**/EXTRACT**|   既存のライブラリのメンバーのコピーが格納されているオブジェクト (.obj) ファイルを作成します。<br/><br/>詳細については、「[ライブラリメンバーの抽出](extracting-a-library-member.md)」を参照してください。|
|**/INCLUDE**|   シンボルをシンボルテーブルに追加します。<br/><br/>詳細については、「[インポートライブラリとエクスポートファイルのビルド](building-an-import-library-and-export-file.md)」を参照してください。|
|**/LIBPATH**|   環境ライブラリ パスをオーバーライドします。<br/><br/>詳細については、「[ライブラリの管理](managing-a-library.md)」を参照してください。|
|**/Link再現**|   .Lib のクラッシュまたは内部エラーを再現するために必要なアーティファクトを作成します。<br/><br/>詳細については、「[LIB の実行](running-lib.md)」を参照してください。|
|**/Linkreprotarget**|   では、指定されたファイルで .lib が使用されている場合にのみ、 **/link再現**アーティファクトが生成されます。<br/><br/>詳細については、「[LIB の実行](running-lib.md)」を参照してください。|
|**/LIST**|   出力ライブラリに関する情報を標準出力に表示します。<br/><br/>詳細については、「[ライブラリの管理](managing-a-library.md)」を参照してください。|
|**/LTCG**|   リンク時のコード生成を使用してライブラリを構築します。<br/><br/>詳細については、「[LIB の実行](running-lib.md)」を参照してください。|
|**/MACHINE**|   プログラムのターゲットプラットフォームを指定します。<br/><br/>詳細については、「[LIB の実行](running-lib.md)」を参照してください。|
|**/NAME**|   インポートライブラリの作成時に、インポートライブラリを作成する DLL の名前を指定します。<br/><br/>詳細については、「[ライブラリの管理](managing-a-library.md)」を参照してください。|
|**/NODEFAULTLIB**|   外部参照を解決するときに検索するライブラリの一覧から、1つまたは複数の既定のライブラリを削除します。<br/><br/>詳細については、「[ライブラリの管理](managing-a-library.md)」を参照してください。|
|**/NOLOGO**|   LIB の著作権メッセージとバージョン番号が表示されないようにし、コマンドファイルがエコーされないようにします。<br/><br/>詳細については、「[LIB の実行](running-lib.md)」を参照してください。|
|**/OUT**|   既定の出力ファイル名をオーバーライドします。<br/><br/>詳細については、「[ライブラリの管理](managing-a-library.md)」を参照してください。|
|**/REMOVE**|   出力ライブラリからオブジェクトを除外します。<br/><br/>詳細については、「[ライブラリの管理](managing-a-library.md)」を参照してください。|
|**/SUBSYSTEM**|   出力ライブラリにリンクすることによって作成されたプログラムを実行する方法をオペレーティングシステムに指示します。<br/><br/>詳細については、「[ライブラリの管理](managing-a-library.md)」を参照してください。|
|**/VERBOSE**|   追加される .obj ファイルの名前など、セッションの進行状況に関する詳細が表示されます。<br/><br/>詳細については、「[LIB の実行](running-lib.md)」を参照してください。|
|**/WX**|   警告をエラーとして扱います。<br/><br/>詳細については、「[LIB の実行](running-lib.md)」を参照してください。|

## <a name="see-also"></a>参照

[LIB リファレンス](lib-reference.md)\
[LIB 入力ファイル](lib-input-files.md)\
[LIB 出力ファイル](lib-output-files.md)\
[その他の LIB 出力](other-lib-output.md)\
[ライブラリの構造](structure-of-a-library.md)
