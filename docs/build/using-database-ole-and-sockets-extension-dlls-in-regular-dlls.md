---
title: レギュラー MFC Dll でのデータベース、OLE、およびソケット MFC 拡張 Dll の使用
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314690"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>レギュラー MFC Dll でのデータベース、OLE、およびソケット MFC 拡張 Dll の使用

MFC 拡張 DLL と有線接続しない場合は、MFC 拡張 DLL からレギュラー MFC DLL を使用する場合、 **CDynLinkLibrary**オブジェクトのチェーン レギュラー MFC DLL の一連の関連する問題の 1 つ以上を実行する場合があります。 MFC データベース、OLE、およびソケットのデバッグ バージョンをサポートするため、Dll が MFC 拡張 Dll として実装されている、明示的に使用、独自の MFC 拡張 Dll のいずれかのしないいなくても、機能をこれらの MFC を使用する場合と同様の問題が発生する可能性があります。 いくつかの現象は次のとおりです。

- クラスの型のオブジェクトを逆シリアル化しようとして定義されている場合、MFC 拡張 DLL、メッセージ"警告。アーカイブから CYourClass を読み込むことができません。 クラス定義されていません。" シリアル化が失敗のトレースのデバッグ ウィンドウとオブジェクトに表示されます。

- 無効なクラスを示す例外がスローする可能性があります。

- MFC 拡張 DLL に格納されているリソースを読み込みが失敗`AfxFindResourceHandle`返します**NULL**または間違ったリソース ハンドル。

- `DllGetClassObject`、 `DllCanUnloadNow`、および`UpdateRegistry`、 `Revoke`、 `RevokeAll`、および`RegisterAll`のメンバー関数`COleObjectFactory`MFC 拡張 DLL で定義されているクラス ファクトリの検索に失敗します。

- `AfxDoForAllClasses` MFC 拡張 DLL 内の任意のクラスには機能しません。

- MFC の標準的なデータベース、ソケット、または OLE リソースを読み込めませんでした。 たとえば、 **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) レギュラー MFC DLL が MFC データベース クラスを使用して正しくときでも、空の文字列を返します。

これらの問題を解決するには作成し、MFC の拡張機能を作成する DLL の初期化関数をエクスポート、 **CDynLinkLibrary**オブジェクト。 MFC 拡張 DLL を使用する各レギュラー MFC DLL から 1 回だけ初期化関数を呼び出し。

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE、MFC データベース (または DAO)、または MFC ソケットのサポート

場合は、MFC OLE、MFC データベース (または DAO) を使用しているか、それぞれ、レギュラー MFC DLL で MFC ソケットのサポート、MFC デバッグ MFC 拡張 Dll MFCOxxD.dll、MFCDxxD.dll、および MFCNxxD.dll (xx はバージョン番号です) が自動的にリンクされます。 使用してこれらの Dll のそれぞれの定義済みの初期化関数を呼び出す必要があります。

データベース サポートについては、追加の呼び出しを`AfxDbInitModule`レギュラー MFC DLL のする`CWinApp::InitInstance`関数。 この呼び出しは、基底クラスに対する呼び出しの前に発生しますまたは、追加の MFCDxxD.dll にアクセスするコードを確認してください。 この関数は、パラメーターを受け取らないし、void を返します。

OLE サポートについては、追加の呼び出しを`AfxOleInitModule`レギュラー MFC DLL のする`CWinApp::InitInstance`します。 なお、 **COleControlModule InitInstance**関数呼び出し`AfxOleInitModule`既に、OLE コントロールを構築してを使用している場合、`COleControlModule`への呼び出しを追加しないでください`AfxOleInitModule`。

ソケットのサポートへの呼び出しを追加`AfxNetInitModule`レギュラー MFC DLL のする`CWinApp::InitInstance`します。

MFC Dll のリリース ビルドしアプリケーションは、ソケット、データベースを個別の Dll を使用しないまたは OLE サポートことに注意してください。 ただし、リリース モードでこれらの初期化関数を呼び出しても安全です。

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary オブジェクト

各このトピックの冒頭で説明されている操作の中に、MFC は、目的の値またはオブジェクトを検索する必要があります。 たとえば、逆シリアル化中に MFC が、適切なランタイム クラスを使用して、アーカイブ内のオブジェクトを一致するように現在使用可能なすべてのランタイム クラスを使用して検索する必要があります。

MFC がのチェーンに、使用中のすべての MFC 拡張 Dll からのスキャンに、これらの検索の一部として**CDynLinkLibrary**オブジェクト。 **CDynLinkLibrary**オブジェクトの構築時にチェーンに自動的にアタッチおよび初期化中にさらに各 MFC 拡張 DLL によって作成されます。 また、(アプリケーションまたはレギュラー MFC DLL) のすべてのモジュールでは、独自のチェーンの**CDynLinkLibrary**オブジェクト。

MFC 拡張 DLL にワイヤード (有線) を取得するため、 **CDynLinkLibrary**チェーンを作成する必要がありますが、 **CDynLinkLibrary** MFC 拡張 DLL を使用するすべてのモジュールのコンテキスト内のオブジェクト。 そのため場合は、MFC 拡張 DLL はレギュラー MFC Dll から使用すると、提供するエクスポートされた初期化関数を作成する、 **CDynLinkLibrary**オブジェクト。 MFC の拡張機能を使用するすべてのレギュラー MFC DLL DLL は、エクスポートされた初期化関数を呼び出す必要があります。

MFC 拡張 DLL はのみを取り上げますレギュラー MFC DLL を決しておよび MFC アプリケーション (.exe) から使用するかどうかは、作成するだけで十分です、 **CDynLinkLibrary** MFC 拡張 DLL 内のオブジェクト`DllMain`します。 これは、MFC DLL ウィザード MFC 拡張 DLL のコードを行っています。 暗黙的に、MFC 拡張 DLL の読み込み時に`DllMain`読み込みをアプリケーションが開始する前に実行します。 すべて**CDynLinkLibrary** MFC DLL が MFC アプリケーションが割り当てている既定のチェーンにワイヤードは作成します。

複数存在することは適切です**CDynLinkLibrary** MFC 拡張 DLL がメモリから動的にアンロードされる場合に特に、すべて 1 つのチェーン内の 1 つの MFC 拡張 DLL からのオブジェクトします。 呼び出さないでください初期化関数は複数回、1 つのモジュールから。

## <a name="sample-code"></a>サンプル コード

このサンプル コードでは、レギュラー MFC DLL が MFC 拡張 DLL にリンクが暗黙的に想定しています。 これは、レギュラー MFC DLL を作成するときに、MFC 拡張 DLL のインポート ライブラリ (.lib) にリンクすることによって実現されます。

MFC 拡張 DLL のソースで、次の行があります。

```
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

インポートできるように、 **InitYourExtDLL**関数。 これは行うことを使用して**方式**または次のように、DLL の .def ファイル内。

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

呼び出しを追加、`InitInstance`のメンバー、 `CWinApp`-派生した MFC 拡張 DLL を使用して各レギュラー MFC DLL 内のオブジェクト。

```
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>実行する操作

- [MFC 拡張 DLL を初期化します。](run-time-library-behavior.md#initializing-extension-dlls)

- [レギュラー MFC Dll を初期化します。](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [MFC 拡張 DLL](extension-dlls.md)

- [MFC と静的にリンクされるレギュラー MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [MFC と動的にリンクされるレギュラー MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL の一部としての MFC の使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [MFC の DLL バージョン](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>関連項目

[MFC 拡張 DLL](extension-dlls.md)
