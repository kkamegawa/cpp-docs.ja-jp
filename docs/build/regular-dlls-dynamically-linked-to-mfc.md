---
title: MFC と動的にリンクされるレギュラー MFC Dll
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 3bfed5f75dab4c501708950fdb99f53c40ec142c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315002"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>MFC と動的にリンクされるレギュラー MFC Dll

MFC DLL が MFC と動的にリンクする、通常は内部的には、MFC を使用する DLL および MFC または非 MFC の実行可能ファイル、DLL からエクスポートされた関数を呼び出すことができます。 名前について説明します、MFC (MFC の共有バージョンとも呼ばれます) のダイナミック リンク ライブラリのバージョンを使ってこのような DLL がビルドされます。 通常、関数は、通常、標準の C インターフェイスを使用して MFC DLL からエクスポートします。

追加する必要があります、 `AFX_MANAGE_STATE` MFC DLL のモジュールの現在の状態を設定すると動的にリンクされるレギュラー MFC Dll でエクスポートされたすべての関数の先頭にします。 これは、DLL からエクスポートされた関数の先頭に次のコード行を追加することで行います。

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

MFC と動的にリンクされている MFC DLL の場合は、通常は、次の機能があります。

- これは、新しい種類の Visual C 4.0 で導入された DLL です。

- クライアント実行可能ファイル (C、C++、Pascal、Visual Basic、および) で; の Dll の使用をサポートする任意の言語で記述できます。これは MFC アプリケーションではありません。

- 静的にリンクされるレギュラー MFC DLL とは異なりこの種類の DLL が MFC DLL (共有 MFC DLL とも呼ばれます) に動的にリンクします。

- この種類の DLL にリンクされている MFC のインポート ライブラリは、MFC 拡張 Dll または MFC DLL を使用してアプリケーションに使用される 1 つと同じです。(D) MFCxx .lib します。

MFC と動的にリンクされている MFC DLL の場合は、通常は、次の要件があります。

- これらの Dll をコンパイルした **_AFXDLL** MFC DLL に動的にリンクされている実行可能ファイルと同様に、定義されています。 **_USRDLL** MFC と静的にリンクされるレギュラー MFC DLL と同じようにも定義します。

- この種類の DLL のインスタンスを作成する必要があります、 `CWinApp`-クラスを派生します。

- この種類の DLL は、 `DllMain` MFC によって提供されます。 内のすべての DLL に固有の初期化コードを配置、`InitInstance`メンバー関数と終了のコードで`ExitInstance`標準 MFC アプリケーションのようにします。

この種の DLL は、MFC のダイナミック リンク ライブラリのバージョンを使用しているために、現在のモジュール状態を DLL の明示的に設定する必要があります。 これを行うには、使用、 [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)マクロのすべての関数の先頭には、DLL からエクスポートします。

レギュラー MFC Dll が必要、`CWinApp`の MFC アプリケーションのように、クラスとそのアプリケーション クラスの 1 つのオブジェクトを派生します。 ただし、 `CWinApp` DLL のオブジェクトには、メイン メッセージ ポンプがない、`CWinApp`アプリケーションのオブジェクト。

なお、 `CWinApp::Run` DLL には、アプリケーションは、メイン メッセージ ポンプを所有しているためのメカニズムは適用されません。 アプリケーションのメイン メッセージ ポンプが DLL エクスポートのルーチンを呼び出すを呼び出す必要があります、DLL、モードレス ダイアログ ボックスが表示されますまたは独自のメイン フレーム ウィンドウ、`CWinApp::PreTranslateMessage`します。

配置のすべての DLL に固有の初期化、`CWinApp::InitInstance`メンバー関数は通常の MFC アプリケーションのようにします。 `CWinApp::ExitInstance`のメンバー関数、`CWinApp`派生クラスが提供されている MFC から呼び出される`DllMain`DLL が読み込まれる前に機能します。

アプリケーションでは、共有 Dll MFCx0.dll と Msvcr*0.dll (、または同様のファイル) を配布する必要があります。

MFC と動的にリンクされている DLL は、MFC を静的にリンクできません。 レギュラー MFC Dll へのリンクをアプリケーションと動的にリンク MFC、その他の DLL と同じようにします。

通常、シンボルは、通常、標準の C インターフェイスを使用して MFC DLL からエクスポートされます。 レギュラー MFC DLL からエクスポートされた関数の宣言は、次のようになります。

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

レギュラー MFC DLL 内のすべてのメモリ割り当てが DLL 内で維持する必要があります。DLL は必要がありますいないに渡すまたは受信呼び出しの実行可能ファイルから、次のいずれか。

- MFC オブジェクトへのポインター

- MFC によって割り当てられたメモリへのポインター

上記のいずれかを実行する必要がある場合、または呼び出し元の実行可能ファイルと DLL の間で MFC の派生オブジェクトを渡す必要がある場合は、MFC 拡張 DLL をビルドする必要があります。

データのコピーを作成する場合にのみ、C ランタイム ライブラリによって、アプリケーションと DLL のポインターを割り当てられたメモリに渡すも安全です。 削除、これらのポインターのサイズを変更またはまたはメモリのコピーを作成せずに使用しない必要があります。

構築されるレギュラー MFC DLL を動的には、MFC とリンク、ときにマクロを使用する必要があります。 [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) MFC モジュール状態を正しく切り替える。 これは、DLL からエクスポートされた関数の先頭に次のコード行を追加することで行います。

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

**AFX_MANAGE_STATE**または MFC 拡張 Dll で MFC を静的にリンクされるレギュラー MFC Dll で、マクロを使用しない必要があります。 詳細については、次を参照してください。 [MFC モジュールの状態データを管理する](../mfc/managing-the-state-data-of-mfc-modules.md)します。

作成、ビルド、およびレギュラー MFC DLL を使用する方法の例は、サンプルを参照してください。[は](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)します。 MFC と動的にリンクされるレギュラー MFC Dll の詳細については、サンプルの要約を"変換を動的にリンクを MFC DLL"というセクションを参照してください。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [レギュラー MFC Dll を初期化します。](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [MFC を動的にリンクされているレギュラー MFC DLL のモジュール状態](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [MFC モジュールの状態データを管理します。](../mfc/managing-the-state-data-of-mfc-modules.md)

- [レギュラー MFC DLL でのデータベース、OLE、およびソケット MFC 拡張 DLL の使用](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [DLL の一部としての MFC の使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>関連項目

[DLL の種類](kinds-of-dlls.md)
