---
title: 例外処理 (MFC)
ms.date: 11/19/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: 7d1be30edec598135eed2a74fca87f1e5444f55d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246731"
---
# <a name="exception-handling-in-mfc"></a>例外処理 (MFC)

この記事では、MFC で使用できる例外処理機構について説明します。 次の2つのメカニズムを使用できます。

- C++例外 (MFC バージョン3.0 以降で使用可能)

- Mfc バージョン1.0 以降で使用できる MFC 例外マクロ

MFC を使用して新しいアプリケーションを作成する場合は、 C++メカニズムを使用する必要があります。 既存のアプリケーションで既にこのメカニズムが広く使用されている場合は、マクロベースのメカニズムを使用できます。

MFC 例外マクロの代わりに、例外C++を使用するように既存のコードを簡単に変換できます。 コードを変換する場合の利点と、そのためのガイドラインについては、「[例外: MFC 例外マクロからの変換](../mfc/exceptions-converting-from-mfc-exception-macros.md)」を参照してください。

MFC 例外マクロを使用して既にアプリケーションを開発している場合は、新しいコードで例外を使用しC++ながら、既存のコードでこれらのマクロを使用し続けることができます。 「[例外: バージョン3.0 での例外マクロの変更」で](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)は、そのためのガイドラインが提供されています。

> [!NOTE]
>  コード内C++で例外処理を有効にするにC++は、プロジェクトの [[プロパティページ](../build/reference/property-pages-visual-cpp.md)] ダイアログボックスC++の C/フォルダーの [コード生成] ページで [例外を有効にする] を選択するか、 [/ehsc](../build/reference/eh-exception-handling-model.md)コンパイラオプションを使用します。

ここでは、次のトピックについて説明します。

- [例外を使用する場合](#_core_when_to_use_exceptions)

- [MFC 例外サポート](#_core_mfc_exception_support)

- [例外に関する参考資料](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a>例外を使用する場合

プログラムの実行中に関数が呼び出されると、通常の実行、エラーの発生、または異常な実行の3つのカテゴリの結果が発生する可能性があります。 各カテゴリについて以下に説明します。

- 通常の実行

   関数は正常に実行され、を返します。 一部の関数は、結果コードを呼び出し元に返します。これは、関数の結果を示します。 有効な結果コードは関数に対して厳密に定義され、関数の結果の範囲を表します。 結果コードは、成功または失敗を示すことも、通常の期待範囲内にある特定の種類の障害を示すこともできます。 たとえば、ファイル状態関数は、ファイルが存在しないことを示すコードを返すことができます。 結果コードは多くの予期される結果の1つを表すため、"エラーコード" という用語は使用されないことに注意してください。

- 間違った実行

   呼び出し元が関数に引数を渡すとき、または不適切なコンテキストで関数を呼び出すと、何らかの誤りが発生します。 このような状況ではエラーが発生し、プログラムの開発中にアサーションによって検出される必要があります。 (アサーションの詳細については、「 [C/C++アサーション](/visualstudio/debugger/c-cpp-assertions)」を参照してください)。

- 異常な実行

   通常とは異なる実行には、メモリ不足や i/o エラーなど、プログラムの制御外の条件が関数の結果に影響を与える状況が含まれます。 異常な状況は、例外をキャッチしてスローすることによって処理する必要があります。

例外の使用は、特に異常な実行に適しています。

##  <a name="_core_mfc_exception_support"></a>MFC 例外サポート

C++例外を直接使用するか、MFC 例外マクロを使用するかにかかわらず、 [CException クラス](../mfc/reference/cexception-class.md)を使用するか、フレームワークまたはアプリケーションによってスローされる可能性のある `CException`派生オブジェクトを使用します。

次の表は、MFC によって提供される定義済みの例外を示しています。

|例外クラス|意味|
|---------------------|-------------|
|[CMemoryException クラス](../mfc/reference/cmemoryexception-class.md)|メモリ不足|
|[CFileException クラス](../mfc/reference/cfileexception-class.md)|ファイルの例外|
|[CArchiveException クラス](../mfc/reference/carchiveexception-class.md)|アーカイブ/シリアル化の例外|
|[CNotSupportedException クラス](../mfc/reference/cnotsupportedexception-class.md)|サポートされていないサービスに対する要求への応答|
|[CResourceException クラス](../mfc/reference/cresourceexception-class.md)|Windows リソース割り当ての例外|
|[CDaoException クラス](../mfc/reference/cdaoexception-class.md)|データベースの例外 (DAO クラス)|
|[CDBException クラス](../mfc/reference/cdbexception-class.md)|データベースの例外 (ODBC クラス)|
|[COleException クラス](../mfc/reference/coleexception-class.md)|OLE 例外|
|[COleDispatchException クラス](../mfc/reference/coledispatchexception-class.md)|ディスパッチ (オートメーション) の例外|
|[CUserException クラス](../mfc/reference/cuserexception-class.md)|メッセージボックスを使用してユーザーに警告し、汎用[CException クラス](../mfc/reference/cexception-class.md)をスローする例外|

MFC はバージョン 3.0 以降、C++ 例外を使用していますが、フォームの C++ 例外に似た古い例外処理マクロを引き続きサポートします。 これらのマクロは新しいプログラミングで推奨されませんが、下位互換性のために引き続きサポートされます。 既にマクロを使用しているプログラムでは、自由に C++ の例外も使用できます。 プリプロセス中、マクロは、Visual C++ C++バージョン2.0 の言語の MSVC 実装で定義されている例外処理キーワードに評価されます。 C++ 例外処理の使用を開始するときは、既存の例外処理マクロをそのまま維持できます。 マクロとC++例外処理の組み合わせ、および新しい機構を使用するように古いコードを変換する方法については、「[例外C++ : mfc マクロと例外](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)および例外の使用[: mfc 例外マクロからの変換](../mfc/exceptions-converting-from-mfc-exception-macros.md)」を参照してください。 以前の MFC 例外マクロを使用している場合、これは C++ の例外のキーワードに評価されます。 「[例外: バージョン3.0 での例外マクロの変更点」を](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)参照してください。 MFC では、「[構造化例外処理](/windows/win32/debug/structured-exception-handling)」で説明されているように、Windows NT 構造化例外ハンドラー (SEH) を直接サポートしていません。

##  <a name="_core_further_reading_about_exceptions"></a>例外に関する参考資料

次の記事では、MFC ライブラリを使用して例外を処理する方法について説明します。

- [例外処理: 例外のキャッチと削除](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [例外処理: 例外の内容の調査](../mfc/exceptions-examining-exception-contents.md)

- [例外処理: 例外処理でのオブジェクトの解放](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [例外処理: 独自関数からの例外のスロー](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [例外処理: データベースの例外](../mfc/exceptions-database-exceptions.md)

- [例外処理: OLE の例外](../mfc/exceptions-ole-exceptions.md)

次の記事では、MFC 例外マクロとC++例外キーワードを比較し、コードをどのように調整できるかを説明します。

- [例外処理: MFC 3.0 での変更点](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [例外処理: 古いコードの変換](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [例外処理: MFC マクロと C++ 例外機構の使用](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>参照

[例外C++とエラー処理に関する最新のベストプラクティス](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[操作方法: 独自のカスタム例外クラスを作成する](https://go.microsoft.com/fwlink/p/?linkid=128045)
