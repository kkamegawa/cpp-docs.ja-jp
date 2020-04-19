---
title: インポートとエクスポート
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220641"
---
# <a name="importing-and-exporting"></a>インポートとエクスポート

パブリック シンボルをアプリケーションにインポートまたは 2 つのメソッドを使用して DLL から関数をエクスポートできます。

- DLL をビルドするときに、モジュール定義 (.def) ファイルを使用します。

- キーワードを使用して **_declspec**または**方式**メイン アプリケーションの関数定義で

## <a name="using-a-def-file"></a>.Def ファイルを使用します。

モジュール定義ファイル (.def) は、テキスト ファイルです。DLL のさまざまな属性を記述する 1 つ以上のモジュール文が含まれています。 使用しない場合 **_declspec**または**方式**DLL の関数をエクスポートする DLL に .def ファイルが必要です。

.Def ファイルを使用する[アプリケーションにインポート](importing-using-def-files.md)または[DLL からエクスポート](exporting-from-a-dll-using-def-files.md)します。

## <a name="using-declspec"></a>_ _Declspec を使用します。

使用する必要はありません **_declspec**そうですが、正しくコンパイルするコードのより優れたコードを生成するコンパイラを使用します。 コンパイラはかどうか、関数が存在する DLL にか、DLL の境界を越える関数呼び出し内に存在するが通常の間接参照のレベルをスキップするコードを生成するために、コンパイラにより決定できるためより優れたコードを生成できません。 ただし、使用する必要があります **_declspec** DLL で使用される変数をインポートします。

適切な .def ファイルの EXPORTS セクションに**方式**は必要ありません。 **方式**.def ファイルを使用せずに、.exe や .dll ファイルから関数をエクスポートする簡単な方法を提供するようになりました。

インポートを修正するタッチする必要がありますページの数を最小限に抑えるには、Win32 のポータブル実行可能ファイルの形式は設計されています。 これを行うには、インポート アドレス テーブルと呼ばれる 1 つの場所で任意のプログラムのすべてのインポート アドレスを配置します。 これにより、インポートにアクセスするときに、1 つまたは 2 つのページを変更するローダーができます。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [アプリケーションへのインポート](importing-into-an-application-using-declspec-dllimport.md)

- [DLL からのエクスポートします。](exporting-from-a-dll.md)

## <a name="see-also"></a>関連項目

[Visual Studio で C/C++ Dll を作成します。](dlls-in-visual-cpp.md)
