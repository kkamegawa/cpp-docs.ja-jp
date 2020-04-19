---
title: 'TN033:テクニカル ノート 33: MFC の DLL バージョン'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: fda256043027dbff249cedf490b150b6ad30a5fb
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611106"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033:テクニカル ノート 33: MFC の DLL バージョン

ここでは、MFCxx.DLL を使用して MFCxxD.DLL (x は MFC のバージョン番号です) は、MFC アプリケーションや MFC 拡張 Dll とダイナミック リンク ライブラリを共有する方法について説明します。 レギュラー MFC Dll の詳細については、次を参照してください。 [MFC DLL の一部として](../mfc/tn011-using-mfc-as-part-of-a-dll.md)します。

このテクニカル ノートには、Dll の 3 つの側面がについて説明します。 最後の 2 つより高度なユーザーのことです。

- [MFC 拡張 DLL をビルドする方法](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [MFC の DLL バージョンを使用する MFC アプリケーションを作成する方法](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [実装は、MFC がダイナミック リンク ライブラリを共有する方法](#_mfcnotes_how_the_mfc30.dll_is_implemented)

(レギュラー MFC DLL と呼ばれます) の非 MFC アプリケーションで使用できる MFC を使用して DLL を構築する場合を参照してください。[テクニカル ノート 11:](../mfc/tn011-using-mfc-as-part-of-a-dll.md)します。

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL サポートの概要:用語とファイル

**レギュラー MFC DLL**:一部の MFC クラスを使用してスタンドアロンの DLL をビルドするのにには、レギュラー MFC DLL を使用します。 アプリまたは DLL の境界を越えてインターフェイスは、"C"インターフェイス、およびクライアント アプリケーションが MFC アプリケーションする必要はありません。

これは、MFC の 1.0 でサポートされている DLL のサポートのバージョンです。 説明されている、[テクニカル ノート 11:](../mfc/tn011-using-mfc-as-part-of-a-dll.md)と MFC Advanced Concepts サンプル[は](../overview/visual-cpp-samples.md)します。

> [!NOTE]
> Visual C バージョン 4.0 の時点で、用語**USRDLL**は廃止され、静的にリンクされるレギュラー MFC DLL によって置き換えられました。 レギュラー MFC と動的にリンクする MFC DLL をビルドすることもできます。

MFC 3.0 (以降)、OLE、およびデータベース クラスを含むすべての新しい機能によりレギュラー MFC Dll をサポートしています。

**AFXDLL**:これは、MFC ライブラリの共有バージョンとも呼ばれます。 これは、MFC 2.0 で追加された新しい DLL サポートです。 MFC ライブラリ自体は、多くの Dll (後述) であり、必要な Dll が動的にリンク、クライアント アプリケーションまたは DLL。 アプリケーションまたは DLL の境界を越えてインターフェイスは、C +/cli MFC クラスのインターフェイス。 クライアント アプリケーションは、MFC アプリケーションである必要があります。 これは MFC 3.0 のすべての機能をサポート (例外。UNICODE がサポートされていませんデータベース クラス用)。

> [!NOTE]
> Visual C バージョン 4.0 の時点でこの種類の DLL と呼びます「拡張 DLL です」

この注を含む MFC DLL を設定する全体を参照する MFCxx.DLL を使用します。

- デバッグ:MFCxxD.DLL (結合) と MFCSxxD.LIB (静的)。

- リリース:(結合) MFCxx.DLL および MFCSxx.LIB (静的)。

- Unicode のデバッグ:(結合) MFCxxUD.DLL と MFCSxxD.LIB (静的)。

- Unicode のリリース:(結合) MFCxxU.DLL と MFCSxxU.LIB (静的)。

> [!NOTE]
> MFCSxx [U] [D] でします。LIB ライブラリ提供されると共に、MFC Dll を共有します。 これらのライブラリには、アプリケーションまたは DLL に静的にリンクする必要がありますコードが含まれています。

アプリケーションのリンクに対応するインポート ライブラリには:

- デバッグ:MFCxxD.LIB

- リリース:MFCxx.LIB

- Unicode のデバッグ:MFCxxUD.LIB

- Unicode のリリース:MFCxxU.LIB

"MFC 拡張 DLL"は、MFCxx.DLL に基づいて構築された DLL (またはその他の MFC Dll を共有する)。 ここは、MFC コンポーネントのアーキテクチャが開始されます。 MFC クラスから便利なクラスを派生するか、または別の MFC のようなツールキットをビルドする場合は、DLL に配置できます。 最終的なクライアント アプリケーションは、DLL として MFCxx.DLL を使用します。 これは、再利用可能なリーフ クラス、再利用可能な基本クラス、および再利用可能なビュー/ドキュメント クラスを許可します。

## <a name="pros-and-cons"></a>長所と短所

MFC の共有バージョンを使用する理由

- 共有ライブラリを使用すると、(ほとんどの MFC ライブラリを使用する最低限のアプリケーションでは 10 K 未満)、小規模なアプリケーションが発生することができます。

- MFC の共有バージョンでは、MFC 拡張 Dll とレギュラー MFC Dll をサポートします。

- MFC の共有ライブラリを使用するアプリケーションの構築は、MFC 自体をリンクするために必要ないため、静的にリンクされた MFC アプリケーションの構築よりも高速です。 これは特に**デバッグ**ビルド リンカーがデバッグ情報を圧縮する必要があります: デバッグ情報を既に含む DLL とリンクでは、アプリケーション内で圧縮するデバッグ情報が少なくします。

使用する理由いない MFC の共有バージョン。

- 共有ライブラリを使用するアプリケーションを配布するには、MFCxx.DLL (など) を出荷することが必要ですので、プログラムからのライブラリです。 MFCxx.DLL は多くの Dll のように自由に再頒布可能パッケージがまだ必要がありますインストール、DLL、セットアップ プログラムで。 さらに、プログラムと MFC Dll 自体の両方に使用される C ランタイム ライブラリを含む、MSVCRTxx.DLL を出荷する必要があります。

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> MFC 拡張 DLL を記述する方法

MFC 拡張 DLL は、クラスと MFC クラスの機能を装飾するために記述された関数を含む DLL です。 MFC 拡張 DLL は、いくつか追加の考慮事項と、アプリケーションを使用する同じ方法で共有 MFC Dll を使用します。

- ビルド プロセスでは、いくつかの追加のコンパイラとリンカーのオプションと MFC の共有ライブラリを使用するアプリケーションの構築に似ています。

- MFC 拡張 DLL がない、 `CWinApp`-クラスを派生します。

- MFC 拡張 DLL は、特殊なを指定する必要があります`DllMain`します。 AppWizard が提供する`DllMain`関数を変更することができます。

- MFC 拡張 DLL は初期化ルーチンを作成する、通常、 `CDynLinkLibrary` MFC 拡張 DLL がエクスポートする場合`CRuntimeClass`es またはアプリケーションにリソース。 派生クラスの`CDynLinkLibrary`MFC 拡張 DLL で、アプリケーションごとのデータを維持しなければならない場合に使用される可能性があります。

これらの考慮事項については、以下で詳しく説明します。 MFC Advanced Concepts サンプルを参照することも必要があります。 [DLLHUSK](../overview/visual-cpp-samples.md)ためを示しています。

- 共有ライブラリを使用してアプリケーションを構築します。 (DLLHUSK します。EXE はに加えてその他の Dll を MFC ライブラリに動的にリンクする MFC アプリケーション) です。

- MFC 拡張 DLL をビルドします。 (特殊なフラグをなどに注意してください`_AFXEXT`MFC 拡張 DLL のビルドで使用されている)

- MFC 拡張 Dll の 2 つの例です。 1 つは、制限付きのエクスポート (TESTDLL1) での MFC 拡張 DLL と全体のクラス インターフェイス (TESTDLL2) をエクスポートするその他の表示の基本構造を示しています。

クライアント アプリケーションと MFC 拡張 Dll の両方には、MFCxx.DLL の同じバージョンを使用する必要があります。 MFC DLL の規則に準拠し、デバッグを提供する必要がありますと小売 (/release) MFC 拡張 DLL のバージョン。 これにより、クライアント プログラムは、アプリケーションのデバッグと製品版の両方のバージョンをビルドし、それらを適切なデバッグまたは製品版のすべての Dll にリンクできます。

> [!NOTE]
>  C++ では、名前変更と、問題をエクスポート、ために、MFC 拡張 DLL からエクスポートの一覧が表示同じ DLL のデバッグとリテール バージョンと Dll のさまざまなプラットフォームのさまざまな場合があります。 小売 MFCxx.DLL が約 2000 エクスポート エントリ ポイントです。デバッグ MFCxxD.DLL が約 3000 エクスポート エントリ ポイント。

### <a name="quick-note-on-memory-management"></a>メモリ管理でのクイック ノート

このノートの末尾近くの「メモリ管理」というタイトルのセクションでは、MFC の共有バージョンを使用して、MFCxx.DLL の実装について説明します。 DLL がここで説明されている MFC 拡張機能だけを実装するために必要な情報。

同じアプリケーションがまるで、MFCxx.DLL およびクライアント アプリケーションのアドレス空間に読み込まれるすべての MFC 拡張 Dll が同じメモリ アロケーター、リソースの読み込みおよびその他の MFC の「グローバル」状態には使用します。 これは、機能は、非 MFC DLL ライブラリと MFC を静的にリンクされるレギュラー MFC Dll は、まったく逆を実行して各 DLL、独自のメモリ プールから割り当てられるをため重要です。

MFC 拡張 DLL は、メモリを割り当て、その他のアプリケーションに割り当てられたオブジェクトにそのメモリできます混在自由に。 また、MFC の共有ライブラリを使用するアプリケーションがクラッシュした場合、オペレーティング システムの保護は、DLL を共有している他の MFC アプリケーションの整合性を維持します。

同様に、リソースの読み込みを現在の実行可能ファイルと同様に、「グローバル」MFC の状態、クライアント アプリケーションとすべて MFC 拡張 Dll だけでなく MFCxx.DLL 自体の間で共有されます。

### <a name="building-an-mfc-extension-dll"></a>MFC 拡張 DLL の構築

AppWizard を使用するには MFC 拡張 DLL プロジェクトを作成し、適切なコンパイラとリンカーの設定が自動的に生成します。 生成しますが、`DllMain`関数を変更することができます。

MFC 拡張 DLL を既存のプロジェクトを変換する場合は、MFC の共有バージョンを使用してアプリケーションを構築するための標準の規則使用を開始から、次の操作します。

- 追加 **/D_AFXEXT**コンパイラ フラグ。 [プロジェクトのプロパティ] ダイアログで C/C++ ノードを選択します。 プリプロセッサのカテゴリを選択します。 追加`_AFXEXT`マクロの定義のフィールドに、セミコロンで区切っての各アイテムを分離します。

- 削除、 **/Gy**コンパイラ スイッチ。 [プロジェクトのプロパティ] ダイアログで C/C++ ノードを選択します。 コード生成のカテゴリを選択します。 「関数レベルのリンクの有効にする」オプションが有効でないことを確認します。 これにより作成を簡単に、リンカーは参照されていない関数を削除しないために、クラスをエクスポートします。 MFC DLL が MFC では、変更を静的にリンクする場合は、元のプロジェクトは、通常の構築に使用、 **/MT [d]** コンパイラ オプションを **/MD [d]** します。

- エクスポート ライブラリをビルド、 **/DLL**リンクするにはオプションです。 これは、新しいターゲットを作成すると、Win32 ダイナミック リンク ライブラリを対象の型として指定するときに設定されます。

### <a name="changing-your-header-files"></a>ヘッダー ファイルの変更

MFC 拡張 DLL の目的は、その機能を使用できる 1 つまたは複数のアプリケーションにいくつかの一般的な機能をエクスポートする通常です。 これを要約するクラスと、クライアント アプリケーションで使用できるグローバル関数をエクスポートします。

これを実行するには、各メンバー関数がマークされているようにインポートまたはエクスポートする適切なを確認する必要があります。 これには、特別な宣言が必要です:`__declspec(dllexport)`と`__declspec(dllimport)`します。 として宣言することが必要なクライアント アプリケーションによって、クラスを使用している場合`__declspec(dllimport)`します。 MFC 拡張 DLL 自体が構築されるときに、として宣言する必要がある`__declspec(dllexport)`します。 さらに、関数は、実際をエクスポート、クライアント プログラムが読み込み時にバインドするようにします。

使用して、クラス全体をエクスポートする`AFX_EXT_CLASS`クラス定義にします。 として framework でこのマクロが定義されている`__declspec(dllexport)`とき`_AFXDLL`と`_AFXEXT`は定義されている、として定義されている`__declspec(dllimport)`とき`_AFXEXT`が定義されていません。 `_AFXEXT` 前述のようは、MFC 拡張 DLL を作成するときにのみ定義されます。 例:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>クラス全体をエクスポートしません。

場合があります、クラスの個々 のために必要なメンバーだけをエクスポートすることがあります。 エクスポートする場合など、 `CDialog`-派生クラスでコンス トラクターをエクスポートする必要がありますのみ、`DoModal`を呼び出します。 DLL を使用してこれらのメンバーをエクスポートすることができます。DEF ファイルを使用できるも`AFX_EXT_CLASS`でほぼ同じ方法で、個々 のメンバーをエクスポートする必要があります。

例:

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

これを行うときに、不要になったクラスのすべてのメンバーをエクスポートするため、その他の問題に実行できます。 問題は、MFC マクロの動作方法です。 MFC のヘルパー マクロのいくつか実際に宣言またはデータ メンバーを定義します。 そのため、これらのデータ メンバーは、DLL からエクスポートする必要があります。

たとえば、DECLARE_DYNAMIC マクロは MFC 拡張 DLL を作成するときに、よう定義します。

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

行を"静的`AFX_DATA`"クラスの内部静的オブジェクトを宣言しています。 このクラスを正しくエクスポートし、クライアントのランタイム情報にアクセスします。EXE、この静的オブジェクトをエクスポートする必要があります。 静的オブジェクトは、修飾子で宣言されているため`AFX_DATA`、のみを定義する必要があります`AFX_DATA`する`__declspec(dllexport)`、DLL のビルド時として定義し、`__declspec(dllimport)`クライアント実行可能ファイルを作成するときにします。

前述したように、`AFX_EXT_CLASS`はこの方法で既に定義されています。 再定義するだけ`AFX_DATA`と同じである`AFX_EXT_CLASS`クラス定義をします。

例:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS
class CExampleView : public CView
{
    DECLARE_DYNAMIC()
    // ... class definition ...
};
#undef  AFX_DATA
#define AFX_DATA
```

常に MFC を使用して、`AFX_DATA`のため、この手法は、このようなシナリオはすべての機能、マクロ、内で定義するデータ項目上のシンボルです。 たとえばは DECLARE_MESSAGE_MAP を動作します。

> [!NOTE]
> クラスの選択したメンバーではなく、クラス全体をエクスポートする場合は、静的データ メンバーが自動的にエクスポートします。

同じ手法を使用するには自動的にエクスポートする、`CArchive`ストリーム マクロを使用するクラスの抽出演算子。 アーカイブの演算子をエクスポートするには、クラス宣言の角かっこ (であります。H ファイル) を次のコード。

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>_AFXEXT の制限事項

_ を使用する**AFXEXT** MFC 拡張 Dll が MFC 拡張 Dll の複数の層があるない限りのプリプロセッサ シンボル。 MFC 拡張 Dll を呼び出すか、独自の MFC 拡張 Dll で、MFC クラスから派生し、クラスから派生した場合は、あいまいさを回避するために独自のプリプロセッサ シンボルを使用する必要があります。

問題は、そので Win32、として任意のデータを明示的に宣言する必要があります`__declspec(dllexport)`、DLL からエクスポートする場合と`__declspec(dllimport)`DLL からインポートする場合。 定義するときに`_AFXEXT`、MFC ヘッダーことを確認します`AFX_EXT_CLASS`が正しく定義されています。

場合などがある複数のレイヤー、1 つの記号`AFX_EXT_CLASS`MFC 拡張 DLL 可能性がある新しいクラスをエクスポートするだけでなく他の MFC 拡張 DLL から他のクラスをインポートするために十分ではありません。 この問題を扱うために、DLL を使用すると、DLL 自体を作成することを示す特殊なプリプロセッサ シンボルを使用します。 たとえば、2 つの MFC 拡張 Dll、A.DLL、B.DLL です。 それらの各ファイルはエクスポート A.H と B.H、一部のクラスです。 B.DLL は、A.DLL からクラスを使用します。 ヘッダー ファイルは次のようになります。

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

A.DLL をビルドするときに構築されて **/DA_IMPL** B.DLL をビルドするときに構築されて、 **/DB_IMPL**します。 DLL ごとに個別のシンボルを使用して CExampleB がエクスポートされ、CExampleA は B.DLL を構築するときにインポートされます。 CExampleA が A.DLL を構築するときにエクスポートし、B.DLL (または他のクライアント) で使用するときをインポートします。

組み込みを使用する場合、この種類の階層化を行うことはできません`AFX_EXT_CLASS`と`_AFXEXT`プリプロセッサ シンボル。 上記で説明した手法では、その OLE、データベース、およびネットワークの MFC 拡張 Dll を構築する際に MFC 自体のメカニズムを使用するいないとは異なりの方法でこの問題は解決します。

### <a name="not-exporting-the-entire-class"></a>クラス全体をエクスポートしません。

ここでも、クラス全体にエクスポートするときに、特別な注意する必要があります。 MFC マクロによって作成されたために必要なデータ項目が正常にエクスポートすることを確認する必要があります。 これは、再定義して行うことができます`AFX_DATA`特定のクラスのマクロにします。 これはクラス全体をエクスポートしない場合はいつ実行する必要があります。

例:

```cpp
// A.H
#ifdef A_IMPL
    #define CLASS_DECL_A  _declspec(dllexport)
#else
    #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
    DECLARE_DYNAMIC()
    CLASS_DECL_A int SomeFunction();
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

MFC 拡張 DLL のメイン ソース ファイルに配置する必要がありますの正確なコードを次に示します。 標準のインクルードした後、その必要があります。 MFC 拡張 DLL のスターター ファイルを作成する AppWizard を使用すると、提供されるに注意してください、`DllMain`できます。

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

呼び出し`AfxInitExtensionModule`モジュールのランタイム クラスをキャプチャ (`CRuntimeClass`構造) とそのオブジェクトのファクトリ (`COleObjectFactory`オブジェクト) 使用するときに後で、`CDynLinkLibrary`オブジェクトが作成されます。 (省略可能) 呼び出し`AfxTermExtensionModule`により、MFC クリーンアップするには MFC 拡張 DLL の各プロセスがデタッチされるとき (プロセスが終了すると、またはの結果として、DLL がアンロードされるときに発生する、`FreeLibrary`呼び出す) MFC 拡張 DLL から。 ほとんどの MFC 拡張 Dll が動的に読み込まれていないため (通常は、リンク、インポート ライブラリを使用して)、呼び出し`AfxTermExtensionModule`は通常必要ありません。

読み込みとするアプリケーションと MFC 拡張 Dll を動的に解放する場合に呼び出してください`AfxTermExtensionModule`上記のようです。 使用してくださいにも`AfxLoadLibrary`と`AfxFreeLibrary`(Win32 関数ではなく`LoadLibrary`と`FreeLibrary`)、アプリケーションが複数のスレッドを使用している場合、または MFC 拡張 DLL を動的に読み込む場合。 使用して`AfxLoadLibrary`と`AfxFreeLibrary`MFC 拡張 DLL が読み込まれ、アンロードされたときに実行されるスタートアップとシャット ダウン コードが MFC のグローバル状態を破損しないことを保証します。

AFXDLLX のヘッダー ファイル。H には定義などの MFC 拡張 Dll で使用される構造の特別な定義が含まれています`AFX_EXTENSION_MODULE`と`CDynLinkLibrary`します。

グローバル*extensionDLL*に示すように宣言する必要があります。 MFC の 16 ビット バージョンとは異なりメモリを割り当てるし、MFCxx.DLL が時間によって完全に初期化されるため、この期間中、MFC 関数を呼び出す、`DllMain`が呼び出されます。

### <a name="sharing-resources-and-classes"></a>リソースやクラスの共有

単純な MFC 拡張 Dll は、クライアント アプリケーションと何も詳細に低帯域幅のいくつかの関数をエクスポートする必要があるだけです。 複数のユーザー インターフェイスの処理を要する Dll は、クライアント アプリケーションにリソースや C++ クラスをエクスポートすることがあります。

リソースのエクスポートには、リソース リストを使います。 各アプリケーションでのシングル リンク リストは、`CDynLinkLibrary`オブジェクト。 リソースを探すときにリソースを読み込む標準の MFC 実装のほとんどはまず、現在のリソース モジュール (`AfxGetResourceHandle`) ウォークが見つからない場合の一覧`CDynLinkLibrary`オブジェクトが要求されたリソースを読み込もうとしています。

C++ のクラス名を指定して C++ オブジェクトの動的作成は似ています。 すべての MFC オブジェクトの逆シリアル化機構が必要な`CRuntimeClass`オブジェクトを登録できるように、以前に格納されたに基づいて必要な型の C++ オブジェクトを動的に作成してそれを再構築できます。

MFC 拡張 DLL であるクラスを使用するクライアント アプリケーションの場合`DECLARE_SERIAL`、クライアント アプリケーションに表示される、クラスをエクスポートする必要があります。 ウォークすることによってこれはまた、`CDynLinkLibrary`一覧。

MFC Advanced Concepts サンプルの場合[DLLHUSK](../overview/visual-cpp-samples.md)の一覧は次のようなもの。

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

MFCxx.DLL は、通常の最後に、リソースやクラス リストです。 MFCxx.DLL には、すべてのプロンプト文字列をすべての標準コマンド Id など、標準 MFC リソースが含まれます。 リストの末尾に置くことにより、Dll としないクライアント アプリケーション自体を独自に依存する、MFCxx.DLL 内の共有リソースには、標準 MFC リソースのコピー。

どのような Id を注意する必要がある欠点や名前を選択するには、クライアント アプリケーションの名前空間にリソースとすべての Dll のクラス名を結合します。 もちろんを無効にできますこの機能によって、いずれかをエクスポートしないリソースまたは`CDynLinkLibrary`をクライアント アプリケーションのオブジェクト。 [DLLHUSK](../overview/visual-cpp-samples.md)サンプルは、複数のヘッダー ファイルを使用して、共有リソースの名前空間を管理します。 参照してください[テクニカル ノート 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)共有リソース ファイルの使用に関するヒントを表示します。

### <a name="initializing-the-dll"></a>DLL の初期化

前述のようは、通常、作成する、`CDynLinkLibrary`クライアント アプリケーションにリソースやクラスをエクスポートするにはオブジェクトです。 DLL を初期化するために、エクスポートされたエントリ ポイントを提供する必要があります。 少なくとも、これは、void のルーチンを引数を受け取らず、nothing を返しますが、どのようなことができます。

DLL を使用する各クライアント アプリケーションは、このアプローチを使用する場合、この初期化ルーチンを呼び出す必要があります。 これを割り当てることがあります`CDynLinkLibrary`オブジェクト、`DllMain`呼び出した後だけ`AfxInitExtensionModule`です。

初期化ルーチンを作成する必要があります、 `CDynLinkLibrary` MFC 拡張 DLL は最大ワイヤード (有線) の現在のアプリケーションのヒープ内のオブジェクト。 これは、次のように実行できます。

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

ルーチンの名前、 *InitXxxDLL*でこの例で使用できます必要なものです。 する必要はありません**extern"C"** はそのによりエクスポートの一覧を管理しやすくします。

> [!NOTE]
> レギュラー MFC DLL から MFC 拡張 DLL を使用する場合は、この初期化関数をエクスポートする必要があります。 この関数は、MFC 拡張 DLL のクラスまたはリソースを使用する前に、レギュラー MFC DLL から呼び出す必要があります。

### <a name="exporting-entries"></a>エントリのエクスポート

クラスをエクスポートして単純な方法は、使用する`__declspec(dllimport)`と`__declspec(dllexport)`各クラスおよびグローバル関数をエクスポートします。 これにより、ずっと簡単になりますが、あまり、どのような関数はエクスポート制御があるし、関数を序数でエクスポートすることはできませんので (後述) の各エントリ ポイントの名前を付けるより非効率です。 TESTDLL1 と TESTDLL2 は、このメソッドを使用して、そのエントリをエクスポートします。

効率的な方法 (および MFCxx.DLL で使用されるメソッド) が内の各エントリの名前を付け、各エントリを手動でエクスポートするのには、します。DEF ファイルです。 Dll の (つまり、いないすべてのプロパティ) を選択的なエクスポートをエクスポートしましたのでどのインターフェイスをエクスポートすることにしましたする必要があります。 内のエントリの形式で、リンカーに完全修飾名を指定する必要がありますのでこれは難しいのです。DEF ファイルです。 シンボリック リンクをある本当に必要でない限り、C++ のクラスをエクスポートしないでください。

しようとした場合のクラスと C++ をエクスポートします。DEF ファイルの前に、この一覧を自動的に生成するツールを開発したい場合があります。 これ行う 2 段階のリンクの処理を使用します。 エクスポートなしで、DLL をリンクし、リンカーが生成します。マップ ファイルです。 します。並べ替え、いくつかのエクスポート エントリを生成する使用できるようにエクスポートする必要がある関数の一覧を生成するマップ ファイルを使用できます、します。DEF ファイルです。 MFCxx.DLL および OLE と数、千、データベースの MFC 拡張 Dll のエクスポートの一覧は、(完全に自動ではなく、いくつか手をしばらくの間でのごとに 1 回のチューニングが必要です) が、このようなプロセスを使用して生成されました。

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs します。CDynLinkLibrary

MFC 拡張 DLL がない、 `CWinApp`-派生した独自のオブジェクトは、機能する必要があります代わりに、 `CWinApp`-クライアント アプリケーションのオブジェクトを派生します。 これは、クライアント アプリケーションがメイン メッセージ ポンプ、アイドル ループをこれに所有していることを意味します。

新しいクラスを派生させることができる場合は、MFC 拡張 DLL は、各アプリケーション用の追加データを維持する必要があります、`CDynLinkLibrary`ルーチンがこれまで説明 InitXxxDLL で作成するとします。 実行すると、DLL がの現在のアプリケーションの一覧を確認できます`CDynLinkLibrary`特定の MFC 拡張 DLL の 1 つを検索するオブジェクト。

### <a name="using-resources-in-your-dll-implementation"></a>DLL の実装でリソースの使用

既定のリソース負荷がの一覧をウォーク前述のように、`CDynLinkLibrary`探している最初の EXE または DLL を要求されたリソースを持つオブジェクト。 すべての MFC Api だけでなく、内部のコードを使用してすべて`AfxFindResourceHandle`にリソースの一覧が存在する場所に関係なく、任意のリソースを検索する方法について説明します。

のみの特定の場所からリソースを読み込む場合は、Api を使用して、`AfxGetResourceHandle`と`AfxSetResourceHandle`古いハンドルを保存し、新しいハンドルを設定します。 クライアント アプリケーションに戻る前に、元のリソース ハンドルを必ず復元してください。 TESTDLL2 サンプルは、メニューを明示的に読み込むため、このアプローチを使用します。

リストを検索する場合、多少速度が低下することとリソース ID 範囲の管理が必要なことが欠点です。 いくつかの MFC 拡張 Dll にリンクするクライアント アプリケーションが DLL のインスタンス ハンドルを指定せずに、任意の DLL で提供されるリソースを使用することの利点があります。 `AfxFindResourceHandle` は、リソース リストを検索して一致するリソースを見つけるのに使われる API です。 リソースの名前と型を受け取り、最初に一致したリソース ハンドル (または NULL) を返します。

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> DLL のバージョンを使用するアプリケーションの作成

### <a name="application-requirements"></a>アプリケーションの要件

MFC の共有バージョンを使用するアプリケーションは、いくつかの単純な規則に従う必要があります。

- 必要があります、`CWinApp`オブジェクトし、メッセージ ポンプの標準の規則に従います。

- 一連の必要なコンパイラ フラグ (下記参照) でコンパイルする必要があります。

- これは、MFCxx インポート ライブラリとリンクする必要があります。 必要なコンパイラ フラグを設定するは、MFC ヘッダーは、どのライブラリがアプリケーションにリンクする必要をリンク時に決定します。

- 実行可能ファイルを実行するには、MFCxx.DLL は、パスまたは Windows システム ディレクトリする必要があります。

### <a name="building-with-the-development-environment"></a>開発環境を構築します。

ほとんどの標準の既定値を内部のメイクファイルを使用している場合は、DLL のバージョンをビルドするプロジェクトを簡単に変更できます。

次の手順では、一部を示しますにリンクされている、正しく機能している MFC アプリケーションがある前提としています。(デバッグ) を LIB および NAFXCW します。(リテール版) の LIB したい場合、MFC ライブラリの共有バージョンを使用するように変換します。 Visual C 環境を実行して、内部のプロジェクト ファイルがあります。

1. **プロジェクト** メニューのをクリックして**プロパティ**します。 **全般**ページ**プロジェクトの既定値**、Microsoft Foundation Classes を設定**共有 DLL で MFC を使用**(MFCxx(d).dll) します。

### <a name="building-with-nmake"></a>NMAKE を使用して構築

コンパイラとリンカーのオプションをサポートするために、メイクファイルを編集する必要があります、Visual C の外部メイクファイルの機能を使用するか、または直接 NMAKE を使用している場合

コンパイラ フラグが必要です。

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

MFC の標準ヘッダーには、このシンボルを定義する必要があります。

- **/MD**アプリケーションは、C ランタイム ライブラリの DLL バージョンを使用する必要があります

その他のすべてのコンパイラ フラグは、MFC の既定値 (たとえば、デバッグ用の _DEBUG) に従います。

リンカーのライブラリのリストを編集します。 変更の一部を示します。LIB MFCxxD.LIB をし NAFXCW を変更します。LIB MFCxx.LIB をします。 LIBC を置き換えます。LIB の各 MSVCRT とします。LIB。 その他の MFC ライブラリによるは MFCxxD.LIB が配置される重要な**する前に**C ランタイム ライブラリ。

必要に応じて追加**用**製品版とデバッグの両方のリソース コンパイラのオプションを (実際に設定されているリソースをコンパイルする 1 つ **/R**)。 これにより、MFC Dll に存在するリソースを共有することで、最終的な実行可能ファイルが小さいにします。

これらの変更を行った後、完全な再構築が必要です。

### <a name="building-the-samples"></a>サンプルのビルド

ほとんどの MFC のサンプル プログラムは、Visual C とは、コマンドラインからの共有 (nmake の) と互換性のあるメイクファイルから構築できます。

MFCxx.DLL を使用するためのサンプルのいずれかに変換するを読み込むことができます、します。MAK は、ファイルを Visual C にし、前述のようにプロジェクト オプションを設定します。 指定できます (nmake の) ビルドを使用しているかどうか、"AFXDLL = 1"、NMAKE でとコマンド ラインがサンプルをビルド共有 MFC ライブラリを使用します。

MFC Advanced Concepts サンプル[DLLHUSK](../overview/visual-cpp-samples.md)が MFC の DLL バージョンを使って構築します。 このサンプルがだけでなく、MFCxx.DLL にリンクされているアプリケーションを構築する方法を示していますが、このテクニカル ノートの後半で説明されている MFC 拡張 Dll などの MFC DLL のパッケージ化オプションの他の機能も示しています。

### <a name="packaging-notes"></a>パッケージのノート

製品版の Dll (MFCxx [U]。DLL) は、自由に再配布します。 Dll のデバッグ バージョンでは、自由に再頒布可能パッケージでないし、アプリケーションの開発時にのみ使用する必要があります。

デバッグ Dll のデバッグ情報が提供されます。 Visual C デバッガーを使用すると、DLL と同様に、アプリケーションの実行をトレースすることができます。 リリース Dll (MFCxx [U]。DLL) デバッグ情報は含まれません。

カスタマイズするか、または Dll を再構築する場合する必要がありますに呼び出しが何か"MFCxx"The MFC SRC ファイル ビルド以外。MAK は、ビルド オプションについて説明し、DLL の名前を変更するためのロジックが含まれています。 これらの Dll が多くの MFC アプリケーションで共有される可能性があるために、ファイル名の変更は必要に応じてです。 MFC Dll の置換のカスタム バージョンを持つ共有 MFC Dll を使用して別の MFC アプリケーションを中断、システムにインストールされている可能性があります。

MFC Dll を再構築することは推奨されません。

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> MFCxx.DLL を実装する方法

次のセクションでは、MFC DLL (MFCxx.DLL および MFCxxD.DLL) を実装する方法について説明します。 について詳細をここもいないすべてを行いたい場合に重要ですが、アプリケーションで MFC DLL を使用します。 ここでは、詳細は MFC 拡張 DLL を記述する方法を理解するために不可欠ですが、この実装の理解に役立つ独自の DLL を作成します。

### <a name="implementation-overview"></a>実装の概要

MFC DLL が MFC 拡張 DLL の特殊なケースでは実際に前述のようです。 非常に多数のクラスの数が多いのエクスポートがあります。 定期的な MFC 拡張 DLL よりもさらに特別なように、いくつかの追加点 MFC DLL で行ってがあります。

### <a name="win32-does-most-of-the-work"></a>Win32 にはほとんどの作業

MFC の 16 ビット バージョンでは、さまざまな特別な手法をアプリごとのデータを含む履歴のセグメント 80x86 アセンブリ コード、プロセスごとの例外のコンテキスト、およびその他の手法によって作成された特別なセグメントが必要です。 Win32 を直接サポート プロセスごとのデータ、DLL のほとんどの場合に必要であります。 ほとんどの MFCxx.DLL は NAFXCW だけです。LIB の DLL にパッケージ化します。 MFC ソース コードを見ると場合に、する必要があるいくつか非常に特殊なケースがあるので、非常にほとんどの #ifdef _AFXDLL にありません。 Win32 Windows 3.1 が (それ以外の場合は Win32s と呼ばれます) の処理には具体的には、特殊なケースです。 Win32s は、MFC DLL がスレッド ローカル ストレージ (TLS) プロセスのローカル データを取得する Win32 Api を使用する必要がありますので直接サポート プロセスごとの DLL データされません。

### <a name="impact-on-library-sources-additional-files"></a>追加のファイル、ライブラリのソースへの影響

影響、 **_AFXDLL**通常の MFC クラス ライブラリのソースとヘッダーのバージョンが比較的重要でないです。 ファイルがある特別なバージョン (AFXV_DLL します。H) だけでなく、追加のヘッダー ファイル (AFXDLL_ します。H) メイン AFXWIN で含まれます。H ヘッダー。 AFXDLL_ します。H ヘッダーが含まれています、`CDynLinkLibrary`クラスとその他の実装の詳細のどちらも`_AFXDLL`アプリケーションや MFC 拡張 Dll。 AFXDLLX します。MFC 拡張 Dll (上記の詳細を参照) を構築するため、H ヘッダーが提供されます。

MFC SRC の MFC ライブラリに通常のソースがあるいくつか追加の条件付きコードの下、 `_AFXDLL` #ifdef します。 追加のソース ファイル (DLLINIT します。CPP) では、余分な DLL の初期化コードなどの MFC の共有バージョンが含まれています。

MFC の共有バージョンを作成するのには、追加のファイルが提供されます。 (以下を参照、DLL をビルドする方法の詳細について。)

- 2 つです。DEF ファイルは、デバッグ (MFCxxD.DEF) 用の MFC DLL のエントリ ポイントのエクスポートに使用し、(MFCxx.DEF) バージョンの DLL を離します。

- します。RC ファイル (ビルドします。RC) には、DLL のすべての標準 MFC リソースと VERSIONINFO リソースが含まれています。

- A。CLW ファイル (ビルドします。MFC の閲覧を許可するクラスの使用の ClassWizard CLW) が提供されます。 注: この機能は MFC の DLL バージョンを特定できません。

### <a name="memory-management"></a>メモリ管理

MFCxx.DLL を使用して、アプリケーションでは、MSVCRTxx.DLL、共有の C ランタイム DLL によって提供される一般的なメモリ アロケーターを使用します。 アプリケーションや MFC 拡張 Dll も、MFC Dll 自体は、共有メモリ アロケーターを使用します。 共有 DLL を使用すると、メモリ割り当てに対して、MFC の Dll は、アプリケーションまたはその逆の場合、後で解放されるメモリを割り当てることができます。 グローバルの C++ をオーバーライドしないでください、アプリケーションと DLL の両方には、同じアロケーターを使用する必要があります、ため**演算子 new**または**delete 演算子**します。 C ランタイムのメモリ割り当てルーチンの残りの部分に同じ規則が適用されます (など**malloc**、 **realloc**、**無料**、およびその他)。

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>序数とクラスの関数および DLL の名前を付ける

使用していません、 `class` **方式**の機能、C++コンパイラ。 代わりに、エクスポートの一覧は、クラス ライブラリのソース (MFCxx.DEF および MFCxxD.DEF) に含まれています。 これら選択のエントリ ポイント (関数とデータ) のセットのみがエクスポートされます。 MFC のプライベートな実装の関数やクラスなどの他の記号はエクスポートされません常駐または非常駐型の名前テーブルでの文字列名を指定せずに序数ですべてのエクスポートが完了します。

使用して`class`**方式**小さい Dll を構築するため、MFC では、既定のメカニズムをエクスポートするような大きな DLL の場合、利用可能な方法が効率性と容量があります制限します。

つまり、すべては、大量のリリースは、約 800 KB 程度実行を損なうことや、読み込み速度なしのみ MFCxx.DLL の機能をパッケージことができます。 MFCxx.DLL はされている 100 K より大きなこの手法でなかったために使用します。 これもできるようになりますの末尾に他のエントリ ポイントを追加します。序数でエクスポートの速度とサイズの効率性を損なうことがなく、単純なバージョン管理を許可する DEF ファイルです。 MFC クラス ライブラリ内のメジャー バージョンの変更履歴は、ライブラリの名前に変更されます。 つまり、MFC30 します。DLL では、MFC クラス ライブラリのバージョン 3.0 を含む再頒布可能 DLL です。 この DLL のアップグレードと答えると、仮想的な MFC 3.1 で DLL を MFC31 という名前になります。DLL 代わりにします。 ここでも、カスタム バージョンの MFC DLL を生成するために、MFC のソース コードを変更する場合は、別の名前 (および可能であれば名前に"MFC"のない) を使用します。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
