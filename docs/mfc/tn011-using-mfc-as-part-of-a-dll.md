---
title: TN011:DLL の構成要素としての MFC
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 753612fae101708dd4f8294db121980b62af30b3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65610947"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011:DLL の構成要素としての MFC

ここでは、標準 MFC Dll では、Windows ダイナミック リンク ライブラリ (DLL) の一部として、MFC ライブラリを使用することについて説明します。 これは、Windows の Dll とそのビルド方法について理解するいると仮定します。 MFC 拡張 Dll については、作成するために、MFC ライブラリの拡張機能を参照してください[MFC の DLL バージョン](../mfc/tn033-dll-version-of-mfc.md)します。

## <a name="dll-interfaces"></a>DLL インターフェイス

レギュラー MFC Dll では、アプリケーションと DLL の間のインターフェイスは、C のような関数または明示的にエクスポートされたクラスで指定されるものとします。 MFC クラスのインターフェイスをエクスポートすることはできません。

DLL とアプリケーションの両方は、MFC を使用する場合、両方がある場合、MFC ライブラリの共有バージョンを使用するか、または、ライブラリのコピーに静的にリンクします。 アプリケーションと DLL 可能性があります両方を使用して、標準のバージョンの MFC ライブラリのいずれか。

レギュラー MFC Dll には、いくつかの利点があります。

- DLL を使用するアプリケーションでは、MFC を使用する必要はありませんし、Visual C アプリケーションである必要はありません。

- MFC と静的にリンクされるレギュラー MFC Dll では、DLL のサイズは、使われ、リンクする MFC および C ランタイム ルーチンのみに依存します。

- MFC と動的にリンクされるレギュラー MFC Dll では、MFC の共有バージョンを使用するとメモリを大幅に節約を重要なことがあります。 ただし、共有 Dll で Mfc を配布する必要があります\<*バージョン*> .dll と Msvvcrt\<*バージョン*> .dll、DLL とします。

- DLL のデザインは、クラスを実装する方法の依存しません。 必要に応じて Api にのみ、DLL の設計をエクスポートします。 その結果、実装が変更された場合、レギュラー MFC Dll が現在も有効です。

- Mfc と静的にリンクされるレギュラー MFC Dll で DLL とアプリケーションの両方で MFC を使用する場合は、アプリケーションを別のバージョンの MFC DLL よりも、またはその逆も問題はありません。 MFC ライブラリは、各 DLL または EXE に静的にリンクが、ために、バージョンに関する質問はありません。

## <a name="api-limitations"></a>API の制限事項

一部の MFC 機能は DLL バージョンは、いずれかの技術的な制限は適用されませんので、それらのサービスは、通常、アプリケーションによって提供されますか。 適用可能でない唯一の関数は、現在のバージョンの MFC では、`CWinApp::SetDialogBkColor`します。

## <a name="building-your-dll"></a>DLL のビルド

MFC では、シンボルに静的にリンクされるレギュラー MFC Dll をコンパイルするときに`_USRDLL`と`_WINDLL`定義する必要があります。 DLL のコードは、次のコンパイラ スイッチを使用してコンパイルすることも必要があります。

- **/D_WINDLL**コンパイルである dll を示します

- **/D_USRDLL**レギュラー MFC DLL をビルドするを指定します。

また、これらのシンボルを定義して、MFC と動的にリンクされるレギュラー MFC Dll をコンパイルするときに、これらのコンパイラ スイッチを使用する必要があります。 さらに、シンボル`_AFXDLL`定義する必要があり、DLL のコードをコンパイルする必要があります。

- **/方法**MFC と動的にリンクされるレギュラー MFC DLL を作成することを指定します。

アプリケーションと DLL の間のインターフェイス (Api) を明示的にエクスポートする必要があります。 、低帯域幅を、インターフェイスを定義して、C インターフェイスだけを使うことをお勧めします。 直接的な C インターフェイスより複雑な C++ クラスよりも管理が容易です。

C および C++ の両方のファイルを含めることができる別のヘッダーには、独自の Api を配置します。 MFC Advanced Concepts サンプルでは、ヘッダー ScreenCap.h を参照してください。[は](../overview/visual-cpp-samples.md)例についてはします。 関数をエクスポートするには、それらを入力、`EXPORTS`モジュール定義ファイルのセクション (します。DEF)、または含める`__declspec(dllexport)`関数の定義にします。 使用`__declspec(dllimport)`クライアント実行可能ファイルにこれらの関数をインポートします。

AFX_MANAGE_STATE マクロは、MFC と動的にリンクされるレギュラー MFC Dll でエクスポートされたすべての関数の先頭に追加する必要があります。 このマクロは、DLL のモジュールの現在の状態を設定します。 このマクロを使用するには、DLL からエクスポートされた関数の先頭に次のコード行を追加します。

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain DllMain を -> します。

MFC ライブラリ定義の標準の Win32`DllMain`エントリ ポイントを初期化する、 [CWinApp](../mfc/reference/cwinapp-class.md)典型的な MFC アプリケーションのようにオブジェクトを派生します。 配置のすべての DLL に固有の初期化、 [InitInstance](../mfc/reference/cwinapp-class.md#initinstance)典型的な MFC アプリケーションと同様のメソッド。

なお、[使わ](../mfc/reference/cwinapp-class.md#run)DLL には、アプリケーションは、メイン メッセージ ポンプを所有しているためのメカニズムは適用されません。 DLL は、モードレス ダイアログ ボックスを表示します。 または、独自のメイン フレーム ウィンドウが、アプリケーションのメイン メッセージ ポンプが呼び出す DLL エクスポートのルーチンを呼び出す必要があります[cwinapp::pretranslatemessage](../mfc/reference/cwinapp-class.md#pretranslatemessage)します。

この関数を使用するのサンプルを参照してください。

`DllMain` MFC には、呼び出す関数、[し](../mfc/reference/cwinapp-class.md#exitinstance)から派生したクラスのメソッド`CWinApp`DLL が読み込まれる前にします。

## <a name="linking-your-dll"></a>DLL のリンク

MFC と静的にリンクされるレギュラー MFC Dll Nafxcwd.lib または Nafxcw.lib および Libcmt.lib をという名前の C ランタイムのバージョンの DLL をリンクする必要があります。 これらのライブラリは、あらかじめ組み込まれており、Visual C のセットアップを実行するときに指定することによってインストールされます。

## <a name="sample-code"></a>サンプル コード

プログラムの完全なサンプルについては MFC Advanced Concepts サンプルを参照してください。 このサンプルで注目する点は次のとおりです。

- コンパイラ フラグは、DLL と、アプリケーションのものは異なります。

- リンクの線とします。DEF ファイルは、DLL と、アプリケーションの場合は異なります。

- DLL を使用するアプリケーションを C++ である必要はありません。

- アプリケーションと DLL の間のインターフェイスには、DLLScreenCap.def と API は C または C++ を使用し、エクスポートされるですが。

次の例は、通常は静的にリンクする MFC DLL で定義されている API を示しています。 この例では、宣言で囲まれた、 `extern "C" { }` C++ ユーザーをブロックします。 これは、いくつかの利点があります。 最初に、その DLL Api から使用できるよう C++ 以外のクライアント アプリケーション。 第 2 に、C++ 名前マングルが適用されないためエクスポート名には、DLL のオーバーヘッドが減少します。 最後に、簡単に明示的に追加する、します。DEF は、名前マングルについて心配する必要はありません (序数でエクスポートする) のファイルします。

```
#ifdef __cplusplus
extern "C" {
#endif  /* __cplusplus */

struct TracerData
{
    BOOL bEnabled;
    UINT flags;
};

BOOL PromptTraceFlags(TracerData FAR* lpData);

#ifdef __cplusplus
}
#endif
```

API で使用される構造体は、MFC クラスから派生していないと、API ヘッダーで定義されます。 これは、DLL と、アプリケーション間のインターフェイスの複雑さを軽減し、DLL を C プログラムから使用できるようにします。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
