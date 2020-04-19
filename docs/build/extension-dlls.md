---
title: 拡張 DLL
ms.date: 05/06/2019
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
ms.openlocfilehash: 55b1e55a9c7bdf6daaff98a7fe3f1a2a55f68334
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220766"
---
# <a name="mfc-extension-dlls"></a>MFC 拡張 Dll

MFC 拡張 DLL は、既存の MFC ライブラリ クラスから派生した再利用可能なクラスを主に実装する DLL です。

MFC 拡張 DLL の特長と必要条件は、以下のとおりです。

- クライアント実行可能ファイルはコンパイルした MFC アプリケーションである必要があります`_AFXDLL`定義します。

- MFC 拡張 DLL は、MFC と動的にリンクされるレギュラー MFC DLL によっても使用できます。

- MFC 拡張 Dll のコンパイルは`_AFXEXT`定義します。 これにより、`_AFXDLL`に定義し、MFC ヘッダー ファイルから適切な宣言を取得することを確認します。 また`AFX_EXT_CLASS`として定義されます`__declspec(dllexport)`DLL のビルド中に、MFC 拡張 DLL のクラスを宣言する、このマクロを使用している場合に必要です。

- MFC 拡張 Dll から派生したクラスをインスタンス化する必要がありますできません`CWinApp`がこのオブジェクトを提供するクライアント アプリケーション (または DLL) に依存する必要があります。

- ただし、MFC 拡張 Dll を提供する必要があります、`DllMain`機能し、必要な初期化の操作を行います。

拡張 DLL は、MFC のダイナミック リンク ライブラリ バージョン (MFC の共有バージョン) を使ってビルドされます。 のみ MFC の実行可能ファイル (アプリケーションまたはレギュラー MFC Dll) は MFC の共有バージョンを使用して作成するには、MFC 拡張 DLL を使用できます。 クライアント アプリケーションと MFC 拡張 DLL の両方が同じバージョンの MFCx0.dll を使用する必要があります。 MFC 拡張 DLL では、MFC から新しいカスタム クラスを派生でき、この拡張バージョンの MFC DLL を呼び出すアプリケーションを提供できます。

また、拡張 DLL を使うと、アプリケーションと DLL の間で MFC の派生オブジェクトをやり取りすることもできます。 やり取りされるオブジェクトに関連付けられたメンバー関数は、そのオブジェクトが作成されたモジュール内にあります。 MFC を自由に渡すことができますので、MFC の共有 DLL バージョンを使用する場合、これらの関数が正しくエクスポート、または MFC の派生オブジェクトのポインター、アプリケーションと MFC 拡張 Dll が読み込まれます。

MFC の拡張 DLL で MFC の共有バージョンを使う方法は、アプリケーションで MFC の共有バージョンを使う方法と同じです。ただし、考慮が必要な点がいくつかあります。

- 拡張 DLL には `CWinApp` 派生オブジェクトがありません。 したがって、クライアント アプリケーションの `CWinApp` 派生オブジェクトを使用する必要があります。 クライアント アプリケーションには、メイン メッセージ ポンプ、アイドル ループなどが備わっています。

- MFC の拡張 DLL は、`AfxInitExtensionModule` 関数内の `DllMain` を呼び出します。 この関数の戻り値をチェックする必要があります。 `AfxInitExtensionModule` から 0 が返されると、`DllMain` 関数から 0 が返されます。

- 作成、 **CDynLinkLibrary** MFC 拡張 DLL をエクスポートする必要がある場合は、初期化中にオブジェクト`CRuntimeClass`オブジェクトやアプリケーションにリソース。

MFC のバージョン 4.0 以前では、このような特徴を持つ DLL を AFXDLL と呼んでいました。 AFXDLL を指す、 `_AFXDLL` DLL のビルド時に定義されているプリプロセッサ シンボル。

MFC の共有バージョン用のインポート ライブラリの名前がで説明されている規則に従って[MFC Dll の名前付け規則](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)します。 Visual Studio には、事前構築済みのバージョン、MFC Dll に加え、多くの非 MFC Dll を使用して、アプリケーションと共に配布するが用意されています。 また、Program Files\Microsoft Visual Studio フォルダーにインストールされている Redist.txt に説明があります。

.def ファイルを使ってエクスポートする場合は、以下のコードをヘッダー ファイルの先頭と末尾に記述します。

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

これら 4 つの行では、MFC 拡張 DLL のコードが正しくコンパイルされることを確認します。 この行を追加しなかった場合は、DLL のコンパイルまたはリンクが正常に処理されない場合があります。

MFC を渡す必要がある場合と、MFC の DLL、DLL からの MFC の派生オブジェクト ポインターは、MFC 拡張 DLL をする必要があります。 やり取りされるオブジェクトに関連付けられたメンバー関数は、そのオブジェクトが作成されたモジュール内にあります。 MFC を自由に渡すことができますので、MFC の共有 DLL バージョンを使用する場合、これらの関数が正しくエクスポート、または MFC の派生オブジェクトのポインター、アプリケーションと MFC 拡張 Dll が読み込まれます。

C++ 名前マングルとエクスポートの問題により、MFC の拡張機能のエクスポート リスト DLL 異なる可能性があります同じ DLL のデバッグとリテール バージョンと Dll のさまざまなプラットフォームです。 リテール版の MFCx0.dll には、約 2,000 のエクスポート エントリ ポイントがあります。また、デバッグ バージョンの MFCx0.dll には、約 3,000 のエクスポート エントリ ポイントがあります。

## <a name="memory-management"></a>メモリ管理

MFCx0.dll とクライアント アプリケーションのアドレス空間に Dll が読み込まれるすべての MFC の拡張機能は、同じメモリ アロケーター、リソースを読み込み、およびその他の MFC のグローバル状態を場合と同様、同じアプリケーションで使用します。 これは、機能は、非 MFC DLL ライブラリやレギュラー MFC Dll は正反対と各 DLL、独自のメモリ プールから割り当てられるため重要です。

MFC 拡張 DLL がメモリを割り当てる場合そのメモリを他のアプリケーションに割り当てられたオブジェクトに混在させることができます自由に。 また、MFC と動的にリンクされたアプリケーションにエラーが発生しても、オペレーティング システムの保護機能によって、DLL を共有している他の MFC アプリケーションの整合性が保持されます。

同じように、リソースの読み込み元である現在の実行可能ファイルなど、他のグローバルな MFC の状態も、クライアント アプリケーションとすべての MFC 拡張 DLL の間および MFCx0.dll 自体の間で共有されます。

## <a name="sharing-resources-and-classes"></a>リソースやクラスの共有

リソースのエクスポートには、リソース リストを使います。 各アプリケーションにはシングル リンク リストが含まれています**CDynLinkLibrary**オブジェクト。 リソースを探すときにリソースを読み込む標準の MFC 実装のほとんどはまず、現在のリソース モジュール (`AfxGetResourceHandle`)、リソースが見つからないかどうか、説明の一覧**CDynLinkLibrary**オブジェクト要求されたリソースをロードしようとしています。

リストを検索する場合、多少速度が低下することとリソース ID 範囲の管理が必要なことが欠点です。 いくつかの MFC 拡張 Dll にリンクするクライアント アプリケーションが DLL のインスタンス ハンドルを指定せずに、任意の DLL で提供されるリソースを使用することの利点があります。 `AfxFindResourceHandle` は、リソース リストを検索して一致するリソースを見つけるのに使われる API です。 リソースの名前と型を受け取り、最初に一致したリソース ハンドル (または NULL) を返します。

リソース リストを検索せず、特定の場所からリソースを読み込む場合は、`AfxGetResourceHandle` 関数を使って古いハンドルを保存し、`AfxSetResourceHandle` 関数を使って新規ハンドルを設定します。 クライアント アプリケーションに戻る前に、元のリソース ハンドルを必ず復元してください。 このメニューを明示的に読み込む方法の例は、Testdll2 .cpp、MFC のサンプルを参照してください。 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)します。

MFC の名前を指定して、MFC オブジェクトを動的に作成する場合も同じです。 MFC オブジェクトの逆シリアル化機構を利用するには、`CRuntimeClass` の全オブジェクトを登録する必要があります。この機構では、要求された型の C++ オブジェクトを、以前に格納された型に基づいて動的に作成し、MFC オブジェクトを再構築します。

場合は、MFC サンプル[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)の一覧は次のようなもの。

```
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE
               |                      |
          TESTDLL2.DLL           TESTDLL2.DLL
               |                      |
          TESTDLL1.DLL           TESTDLL1.DLL
               |                      |
           MFCOxxD.DLL                |
               |                      |
           MFCDxxD.DLL                |
               |                      |
            MFCxxD.DLL            MFCxx.DLL
```

場所*xx* ; バージョン番号は、たとえば、42 はバージョン 4.2 を表します。

MFCxx.dll は、通常、リソース リストやクラス リストの最後にあります。 MFCxx.dll には、標準コマンド ID に対応するプロンプト文字列など、すべての標準 MFC リソースが含まれています。 したがって、この DLL をリストの最後に置くと、DLL とクライアント アプリケーションでは標準 MFC リソースの独自のコピーを持つ必要がなくなり、MFCxx.dll 内の共有リソースに依存できるようになります。

すべての DLL のリソース名とクラス名をクライアント アプリケーションの名前空間に結合した場合は、ID や名前を選択するときに注意が必要です。

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)サンプルは、複数のヘッダー ファイルを使用して、共有リソースの名前空間を管理します。

新しいクラスを派生させることができる場合は、MFC 拡張 DLL は、各アプリケーション用の追加データを維持する必要があります、 **CDynLinkLibrary**で作成および`DllMain`します。 実行すると、DLL がの現在のアプリケーションの一覧を確認できます**CDynLinkLibrary**特定の MFC 拡張 DLL の 1 つを検索するオブジェクト。

### <a name="what-do-you-want-to-do"></a>実行する操作

- [MFC 拡張 DLL を初期化します。](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [共有リソース ファイルの使用に関するヒント](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [MFC の DLL バージョン](../mfc/tn033-dll-version-of-mfc.md)

- [MFC と静的にリンクされるレギュラー MFC の Dll](regular-dlls-statically-linked-to-mfc.md)

- [MFC と動的にリンクされるレギュラー MFC の Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [レギュラー MFC DLL でのデータベース、OLE、およびソケット MFC 拡張 DLL の使用](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>関連項目

[Visual Studio で C/C++ Dll を作成します。](dlls-in-visual-cpp.md)
