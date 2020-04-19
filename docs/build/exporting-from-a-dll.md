---
title: DLL からのエクスポート
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196743"
---
# <a name="exporting-from-a-dll"></a>DLL からのエクスポート

.DLL のレイアウトは .exe ファイルとよく似ていますが、重要な相違点が 1 つあります。DLL ファイルには、エクスポート テーブルが含まれています。 エクスポート テーブルには、DLL が別の実行形式に対してエクスポートする各関数の名前が含まれています。 これらの関数は、DLL のエントリ ポイントです。エクスポート テーブルに記述されたエクスポート関数のみが、別の実行形式にアクセスできます。 DLL 内のその他の関数は、その DLL でしか使えません。 DLL のエクスポート テーブルを使用して表示することができます、 [DUMPBIN](reference/dumpbin-reference.md)ツールに/EXPORTS オプション。

DLL から関数をエクスポートする方法には、次の 2 つがあります。

- モジュール定義 (.def) ファイルを作成し、DLL をビルドするときに .def ファイルを使用します。 このアプローチを使用する場合[名前ではなく序数で DLL から関数をエクスポート](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)します。

- キーワードを使用して**方式**関数の定義にします。

いずれかの方法で関数をエクスポートするときに必ず使用して、 [_ _stdcall](../cpp/stdcall.md)呼び出し規約。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [.Def ファイルを使った DLL からエクスポートします。](exporting-from-a-dll-using-def-files.md)

- [関数を使った DLL からエクスポートします。](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS を使ったエクスポート/インポート](exporting-and-importing-using-afx-ext-class.md)

- [C 言語の実行可能ファイルで使用するための C++ 関数をエクスポートします。](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C または C++ 言語の実行可能ファイルで使用するための C 関数をエクスポートします。](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [名前ではなく序数で DLL から関数をエクスポートします。](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [エクスポート方式の使用](determining-which-exporting-method-to-use.md)

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [DLL を初期化します。](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [アプリケーションへのインポート](importing-into-an-application.md)

- [インライン関数のインポートとエクスポート](importing-and-exporting-inline-functions.md)

- [相互インポート](mutual-imports.md)

## <a name="see-also"></a>関連項目

[インポートとエクスポート](importing-and-exporting.md)
