---
title: MFC と静的にリンクされるレギュラー MFC Dll
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314781"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>MFC と静的にリンクされるレギュラー MFC Dll

MFC DLL が MFC と静的にリンクする、通常は内部的には、MFC を使用する DLL および MFC または非 MFC の実行可能ファイル、DLL からエクスポートされた関数を呼び出すことができます。 名前について説明します、MFC のスタティック リンク ライブラリのバージョンを使ってこのような DLL がビルドされます。 通常、関数は、通常、標準の C インターフェイスを使用して MFC DLL からエクスポートします。 作成、ビルド、およびレギュラー MFC DLL を使用する方法の例は、サンプルを参照してください。[は](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)します。

USRDLL という用語は、Visual C のドキュメントでは使用されなくに注意してください。 MFC と静的にリンクされるレギュラー MFC DLL は、USRDLL と同じ特性を持ちます。

Mfc と静的にリンクされるレギュラー MFC DLL には、次の機能があります。

- クライアント実行可能ファイル (C、C++、Pascal、Visual Basic、および) で; の Dll の使用をサポートする任意の言語で記述できます。これは MFC アプリケーションではありません。

- DLL は、アプリケーションで使用される同じ MFC スタティック リンク ライブラリにリンクできます。 Dll をスタティック リンク ライブラリの別のバージョンではなくなりました。

- MFC のバージョン 4.0 の前に、として、Usrdll には、同じ種類の MFC と静的にリンクされるレギュラー MFC の Dll としての機能が用意されています。 Visual C バージョン 4.0 では、USRDLL という用語は廃止されています。

Mfc と静的にリンクされるレギュラー MFC DLL には、次の要件があります。

- この種類の DLL から派生したクラスのインスタンスを作成する必要があります`CWinApp`します。

- この種類の DLL は、 `DllMain` MFC によって提供されます。 内のすべての DLL に固有の初期化コードを配置、`InitInstance`メンバー関数と終了のコードで`ExitInstance`標準 MFC アプリケーションのようにします。

- まだを定義する必要がある、用語 USRDLL は廃止されていますが、"**_USRDLL**"コンパイラのコマンドラインでします。 この定義は、宣言が MFC ヘッダー ファイルからプルされたかを判断します。

レギュラー MFC Dll が必要、`CWinApp`の MFC アプリケーションのように、クラスとそのアプリケーション クラスの 1 つのオブジェクトを派生します。 ただし、 `CWinApp` DLL のオブジェクトには、メイン メッセージ ポンプがない、`CWinApp`アプリケーションのオブジェクト。

なお、 `CWinApp::Run` DLL には、アプリケーションは、メイン メッセージ ポンプを所有しているためのメカニズムは適用されません。 DLL は、モードレス ダイアログまたは、独自のメイン フレーム ウィンドウには、アプリケーションのメイン メッセージ ポンプが呼び出す DLL のエクスポート ルーチンを呼び出す必要があります、 `CWinApp::PreTranslateMessage` DLL のアプリケーション オブジェクトのメンバー関数。

この関数の例ではサンプルを参照してください。

通常、シンボルは、通常、標準の C インターフェイスを使用して MFC DLL からエクスポートされます。 レギュラー MFC DLL からエクスポートされた関数の宣言は次のようになります。

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

レギュラー MFC DLL 内のすべてのメモリ割り当てが DLL 内で維持する必要があります。DLL は必要がありますいないに渡すまたは受信呼び出しの実行可能ファイルから、次のいずれか。

- MFC オブジェクトへのポインター

- MFC によって割り当てられたメモリへのポインター

上記のいずれかまたは呼び出し元の実行可能ファイルと DLL の間で MFC の派生オブジェクトを渡す必要がある必要がある場合は、MFC 拡張 DLL をビルドする必要があります。

データのコピーを作成する場合にのみ、C ランタイム ライブラリによって、アプリケーションと DLL のポインターを割り当てられたメモリに渡すも安全です。 削除、これらのポインターのサイズを変更またはまたはメモリのコピーを作成せずに使用しない必要があります。

MFC と静的にリンクされている DLL は、共有 MFC Dll に動的にリンクできません。 MFC と静的にリンクする DLL がその他の DLL と同じようにアプリケーションを動的にバインドされています。アプリケーションは、その他の DLL と同じようにリンクします。

標準の MFC のスタティック リンク ライブラリの名前がで説明されている規則に従って[MFC Dll の名前付け規則](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)します。 ただし、mfc バージョン 3.0 以降でリンクする MFC ライブラリのバージョンをリンカーに手動で指定する必要は不要になった。 代わりに、MFC ヘッダー ファイルを自動的に決定に基づいてプリプロセッサでリンクする MFC ライブラリの正しいバージョンを定義するよう **\_デバッグ** または **_UNICODE** します。 MFC ヘッダー ファイルでは、特定のバージョンの MFC ライブラリにリンクする、リンカーに指示する/DEFAULTLIB ディレクティブを追加します。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [レギュラー MFC Dll を初期化します。](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [DLL の一部としての MFC の使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [レギュラー MFC DLL でのデータベース、OLE、およびソケット MFC 拡張 DLL の使用](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [MFC DLL を作成します。](../mfc/reference/mfc-dll-wizard.md)

- [MFC と動的にリンクされるレギュラー MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 拡張 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>関連項目

[DLL の種類](kinds-of-dlls.md)
