---
title: 診断サービス
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
ms.openlocfilehash: dbb243453b6d869082a4232b12b27f5510d84aa5
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657631"
---
# <a name="diagnostic-services"></a>診断サービス

Microsoft Foundation Class ライブラりは、プログラムのデバッグをより簡単にする多くの診断サービスを提供します。 これらの診断サービスには、プログラムのメモリー割り当てを追跡したり、実行時にオブジェクトの内容をダンプしたり、実行時にデバッグ メッセージを表示したりできるようにするマクロやグローバル関数が含まれます。 診断サービスのマクロとグローバル関数は、次のカテゴリに分類されます。

- 汎用診断マクロ

- 汎用診断関数と変数

- オブジェクト診断関数

これらのマクロと関数は、MFC のデバッグ バージョンとリリース バージョンの `CObject` から派生するすべてのクラスで使用できます。 ただし、DEBUG_NEW と検証を除くすべてのリリース バージョンで何もありません。

デバッグ ライブラリ内の割り当てられるすべてのメモリ ブロックは、一連の "ガード バイト" で囲まれます。 これらのバイトが間違ったメモリ書き込みによって乱される場合、診断ルーチンが問題を報告できます。 行:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

実装ファイル内に呼び出しはすべて**新しい**メモリの割り当てが行われたファイル名と行の数を格納します。 関数 [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) は、この追加情報を表示して、メモリ リークを識別できるようにします。 診断出力の追加情報については、クラス [CDumpContext](../../mfc/reference/cdumpcontext-class.md) も参照してください。

さらに、C ランタイム ライブラリは、アプリケーションのデバッグに使用できる診断関数のセットもサポートしています。 詳細については、『ランタイム ライブラリ リファレンス』の「 [デバッグ ルーチン](../../c-runtime-library/debug-routines.md) 」を参照してください。

### <a name="mfc-general-diagnostic-macros"></a>MFC 汎用診断マクロ

|||
|-|-|
|[ASSERT](#assert)|メッセージを表示し、ライブラリのデバッグ バージョンで FALSE に指定された式が評価された場合、プログラムを中止します。|
|[ASSERT_KINDOF](#assert_kindof)|オブジェクトが、指定されたクラスのオブジェクト、または指定されたクラスから派生したクラスのオブジェクトであることをテストします。|
|[ASSERT_VALID](#assert_valid)|その `AssertValid` メンバー関数 (通常は `CObject`からオーバーライドされる) を呼び出すことにより、オブジェクトの内部の有効性をテストします。|
|[DEBUG_NEW](#debug_new)|デバッグ モードのすべてのオブジェクト割り当てにファイル名と行番号を指定します。これは、メモリー リークを見つけるのに役立ちます。|
|[DEBUG_ONLY](#debug_only)|ASSERT に似ていますが、式の値のテストデバッグ モードでのみ実行されるコードに役立ちます。|
|[確認し、ENSURE_VALID](#ensure)|データの正確性の検証に使用します。|
|[THIS_FILE](#this_file)|コンパイルされるファイルの名前に展開されます。|
|[TRACE](#trace)|ライブラリのデバッグ バージョンで `printf`に類似した機能を提供します。|
|[VERIFY](#verify)|ASSERT と似ていますとデバッグ バージョンでも、ライブラリのリリース バージョンで式を評価します。|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 汎用診断関数と変数

|||
|-|-|
|[afxDump](#afxdump)|デバッガー出力ウィンドウまたはデバッグ端末に [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 情報を送信するグローバル変数。|
|[afxMemDF](#afxmemdf)|デバッグ メモリ アロケーターの動作を制御するグローバル変数。|
|[AfxCheckError](#afxcheckerror)|そうである場合と、エラーがある場合に渡された SCODE をテストするためのグローバル変数は、適切なエラーをスローします。|
|[AfxCheckMemory](#afxcheckmemory)|現在割り当てられているすべてのメモリの整合性を確認します。|
|[AfxDebugBreak](#afxdebugbreak)|実行中、中断をされます。|
|[AfxDump](#cdumpcontext_in_mfc)|デバッガーにある間に呼び出さると、デバッグ中にオブジェクトの状態をダンプします。|
|[AfxDump](#afxdump)|デバッグ中に、オブジェクトの状態をダンプする内部関数です。|
|[AfxDumpStack](#afxdumpstack)|現在のスタックのイメージを生成します。 この関数は、常に、静的にリンクされます。|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|メモリ リーク ダンプを有効にします。|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|メモリのトラッキングをオンまたはオフにします。|
|[AfxIsMemoryBlock](#afxismemoryblock)|メモリ ブロックが正しく割り当てられていることを確認します。|
|[AfxIsValidAddress](#afxisvalidaddress)|メモリ アドレスの範囲がプログラムの境界内にあることを確認します。|
|[AfxIsValidString](#afxisvalidstring)|文字列へのポインターが有効かどうかを判断します。|
|[AfxSetAllocHook](#afxsetallochook)|各メモリ割り振りでの関数の呼び出しを有効にします。|

### <a name="mfc-object-diagnostic-functions"></a>MFC オブジェクト診断関数

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|ランタイム型チェックをサポートする `CObject`から派生したすべてのクラスで、指定された関数を実行します。|
|[AfxDoForAllObjects](#afxdoforallobjects)|`CObject`new **で割り振られたすべての**から派生したオブジェクトで、指定された関数を実行します。|

### <a name="mfc-compilation-macros"></a>MFC コンパイル マクロ

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|コンパイラの警告を非推奨の MFC 関数の使用を抑制します。|

## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS

コンパイラの警告を非推奨の MFC 関数の使用を抑制します。

### <a name="syntax"></a>構文

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>例

このコード サンプルで、_AFX_SECURE_NO_WARNINGS が定義されていない場合、コンパイラの警告が生じる場合があります。

```cpp
// define this before including any afx files in stdafx.h
#define _AFX_SECURE_NO_WARNINGS
```
```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a> AfxDebugBreak

中断の原因には、この関数を呼び出す (への呼び出しの位置にある`AfxDebugBreak`)、MFC アプリケーションのデバッグ バージョンの実行にします。

### <a name="syntax"></a>構文

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Remarks

`AfxDebugBreak` MFC アプリケーションのリリース バージョンに影響を与えませんし、削除する必要があります。 この関数は、MFC アプリケーションでのみ使用する必要があります。 Win32 API のバージョンを使用して、 `DebugBreak`、非 MFC アプリケーションで中断が発生します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxver_.h

##  <a name="assert"></a>  ASSERT

引数を評価します。

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>パラメーター

*ブール式*<br/>
(ポインターの値を含む) または 0 以外に評価される式を指定します。

### <a name="remarks"></a>Remarks

結果が 0 の場合、マクロは診断メッセージを表示し、プログラムを中止します。 条件が 0 以外の場合は、何もしません。

診断メッセージにフォームがあります

`assertion failed in file <name> in line <num>`

場所*名前*、ソース ファイルの名前を指定および*num*ソース ファイルで失敗したアサーションの行番号です。

MFC のリリース バージョンでは、アサートは、式は評価されず、ので、プログラムは停止しません。 環境に関係なく、式を評価する必要がある場合、は、ASSERT の代わりに確認してくださいマクロを使用します。

> [!NOTE]
>  この関数は、MFC のデバッグ バージョンでのみ使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="assert_kindof"></a>  ASSERT_KINDOF

このマクロは、ポイントされるオブジェクトは、指定したクラスのオブジェクトまたはが指定したクラスから派生したクラスのオブジェクトをアサートします。

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>パラメーター

*classname*<br/>
名前、 `CObject`-クラスを派生します。

*pobject*<br/>
クラス オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

*Pobject*パラメーターがオブジェクトへのポインターにする必要がありますでき**const**します。 オブジェクトが指すし、クラスをサポートする必要があります`CObject`ランタイム クラス情報。 たとえば、ことを確認する`pDocument`のオブジェクトへのポインター、`CMyDoc`クラス、またはその派生物のいずれかをコーディングできます。

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

使用して、`ASSERT_KINDOF`マクロは、コーディングと同じでは正確に。

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

この関数の動作で宣言されたクラスに対してのみ、[DECLARE_DYNAMIC] (実行の時間-オブジェクト-モデル-services.md #declare_dynamic または[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)マクロ。

> [!NOTE]
>  この関数は、MFC のデバッグ バージョンでのみ使用できます。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="assert_valid"></a>  ASSERT_VALID

使用すると、オブジェクトの内部状態の有効性に関する仮定をテストします。

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>パラメーター

*pObject*<br/>
派生したクラスのオブジェクトを指定します`CObject`のオーバーライドのバージョンを持つ、`AssertValid`メンバー関数。

### <a name="remarks"></a>Remarks

ASSERT_VALID 呼び出し、`AssertValid`オブジェクトのメンバー関数は、その引数として渡されます。

MFC のリリース バージョンでは ASSERT_VALID は何も行いません。 デバッグ バージョンでは、ポインターを検証、null の場合、照合チェックに、オブジェクトの独自の呼び出し`AssertValid`メンバー関数。 同じ方法で警告メッセージが表示される場合、これらのいずれかのテストの失敗は、 [ASSERT](#assert)します。

> [!NOTE]
>  この関数は、MFC のデバッグ バージョンでのみ使用できます。

詳細と例については、次を参照してください。 [MFC アプリケーションのデバッグ](/visualstudio/debugger/mfc-debugging-techniques)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW

メモリ リークの検出を支援します。

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Remarks

DEBUG_NEW をあらゆる場所で使用するには通常使用するプログラムで、**新しい**ヒープ領域を割り当てる演算子。

デバッグ モードで (ときに、 **_DEBUG**シンボルが定義されている)、DEBUG_NEW の追跡を割り当てた各オブジェクトのファイル名と行番号。 次に、使用、 [cmemorystate::dumpallobjectssince](cmemorystate-structure.md#dumpallobjectssince)メンバー関数は、DEBUG_NEW で割り当てられた各オブジェクトと共にが表示される、ファイル名と行番号が割り当てられています。

DEBUG_NEW を使用するには、ソース ファイルに次のディレクティブを挿入します。

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

使用する場合に、プリプロセッサが DEBUG_NEW を挿入後、このディレクティブを挿入すると、**新しい**MFC は残りの部分とします。 プログラムのリリース バージョンをコンパイルするときに debug_new を単純な**新しい**操作、およびファイル名と行番号の情報は生成されません。

> [!NOTE]
>  配置に必要な (4.1 以降) の MFC の以前のバージョンで、 `#define` IMPLEMENT_DYNCREATE または IMPLEMENT_SERIAL マクロと呼ばれるすべてのステートメントの後のステートメント。 これは、必要はなくなりました。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY

デバッグ モードで (ときに、 **_DEBUG**シンボルが定義されている)、DEBUG_ONLY 引数を評価します。

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Remarks

リリース ビルドで DEBUG_ONLY では、引数は評価されません。 これは、機能は、デバッグ ビルドでのみ実行する必要があるコードがある場合に便利です。

DEBUG_ONLY マクロでは、周囲に相当*式*で`#ifdef _DEBUG`と`#endif`します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

### <a name="ensure"></a>  確認し、ENSURE_VALID

データの正確性の検証に使用します。

### <a name="syntax"></a>構文

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>パラメーター

*ブール式*<br/>
テストするブール式を指定します。

### <a name="remarks"></a>Remarks

これらのマクロの目的は、パラメーターの検証を向上させることです。 マクロでは、不正確なパラメーターが、コード内の処理を続行しないようにします。 ASSERT マクロとは異なりは、確認マクロは、アサーションを生成するだけでなく例外をスローします。

マクロは、プロジェクトの構成に従って、2 つの方法で動作します。 マクロは、アサートを呼び出すし、アサーションが失敗した場合に例外をスローします。 そのため、デバッグ構成で (_DEBUG が定義されている) 場合は、マクロはアサーションとリリース構成では、マクロの生成中に例外のみ、例外発生 (アサートはリリース構成内の式は評価されません)。

マクロを確認してくださいマクロよう ENSURE_ARG に機能します。

ENSURE_VALID は、ASSERT_VALID マクロ (これは、デバッグ ビルドでのみ効果があります) を呼び出します。 さらに、ポインターが NULL の場合、ENSURE_VALID は例外をスローします。 NULL のテストは、デバッグとリリースの両方の構成で実行されます。

これらのテストのいずれかが失敗した場合、アサートと同様に、警告メッセージが表示されます。 マクロは、必要な場合、無効な引数の例外をスローします。
### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

### <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)<br/>
[VERIFY](#verify)<br/>
[ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE

コンパイルされるファイルの名前に展開されます。

### <a name="syntax"></a>構文

```
THIS_FILE
```

### <a name="remarks"></a>Remarks

情報は、アサートと検証のマクロによって使用されます。 アプリケーション ウィザードとコード ウィザードでは、ソース コード ファイルを作成するにマクロを配置します。

### <a name="example"></a>例

```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the
// compiler recognizes.
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

### <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)<br/>
[ASSERT](#assert)<br/>
[VERIFY](#verify)

##  <a name="trace"></a>  TRACE

指定した文字列を現在のアプリケーションのデバッガーに送信します。

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Remarks

参照してください[ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2)トレースの説明についてはします。 トレースと ATLTRACE2 同じ動作があります。

MFC のデバッグ バージョンでは、このマクロは、現在のアプリケーションのデバッガーに、指定した文字列を送信します。 リリース ビルドでは、このマクロは、(コードが生成されないすべての) nothing にコンパイルします。

詳細については、次を参照してください。 [MFC アプリケーションのデバッグ](/visualstudio/debugger/mfc-debugging-techniques)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="verify"></a>  VERIFY

MFC のデバッグ バージョンでは、その引数を評価します。

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>パラメーター

*ブール式*<br/>
(ポインターの値を含む) または 0 以外に評価される式を指定します。

### <a name="remarks"></a>Remarks

結果が 0 の場合、マクロは診断メッセージを表示し、プログラムが一時停止します。 条件が 0 以外の場合は、何もしません。

診断メッセージにフォームがあります

`assertion failed in file <name> in line <num>`

場所*名前*ソース ファイルの名前を指定および*num*ソース ファイルで失敗したアサーションの行番号です。

MFC のリリース バージョンで式が評価を確認してくださいが印刷またはしませんプログラムを中断します。 たとえば、式が関数呼び出しの場合、呼び出しになります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (MFC の CDumpContext)

アプリケーションでの基本的なオブジェクト ダンプ機能を提供します。

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Remarks

`afxDump` 定義済み[CDumpContext](../../mfc/reference/cdumpcontext-class.md)オブジェクトを送信することができます`CDumpContext`デバッガー出力ウィンドウまたはデバッグ端末の情報。 通常を指定する`afxDump`へのパラメーターとして`CObject::Dump`します。

Windows NT とすべてのバージョンの Windows、`afxDump`アプリケーションをデバッグする場合、Visual C のデバッグ出力ウィンドウに出力が送信されます。

この変数は、MFC のデバッグ バージョンでのみ定義されます。 詳細については`afxDump`を参照してください[MFC アプリケーションのデバッグ](/visualstudio/debugger/mfc-debugging-techniques)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

## <a name="afxdump"></a> AfxDump (内部)

MFC を使用してデバッグ中に、オブジェクトの状態をダンプする内部関数です。

### <a name="syntax"></a>構文

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>パラメーター

*私書箱*<br/>
派生したクラスのオブジェクトへのポインター`CObject`します。

### <a name="remarks"></a>Remarks

`AfxDump` オブジェクトの呼び出し`Dump`メンバー関数を指定した場所に情報の送信、`afxDump`変数。 `AfxDump` MFC のデバッグ バージョンでのみ使用できます。

プログラム コードは呼び出さないでください`AfxDump`、代わりに呼び出す必要がありますが、`Dump`適切なオブジェクトのメンバー関数。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

### <a name="see-also"></a>関連項目

[CObject::Dump](cobject-class.md#dump)

##  <a name="afxmemdf"></a>  afxMemDF

この変数は、デバッガーまたはプログラムからアクセス可能な割り当ての診断を調整することができます。

```
int  afxMemDF;
```

### <a name="remarks"></a>Remarks

`afxMemDF` 列挙体によって指定される次の値を持つことができます`afxMemDF`:

- `allocMemDF` デバッグのアロケーター (デバッグ ライブラリの既定の設定) をオンにします。

- `delayFreeMemDF` 遅延のメモリを解放します。 プログラムがメモリ ブロックを解放中に、アロケーターでは、基になるオペレーティング システムには、そのメモリは返しません。 これにより、最大のメモリ負荷が、プログラムで配置されます。

- `checkAlwaysMemDF` 呼び出し`AfxCheckMemory`たびにメモリを割り当てまたは解放します。 これは、メモリ割り当てと解放が大幅に低下します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError

この関数は、これがエラーであるかどうかを渡された SCODE をテストします。

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Remarks

エラーがある場合、関数は例外をスローします。 渡された SCODE が E_OUTOFMEMORY の場合は、関数、 [CMemoryException](../../mfc/reference/cmemoryexception-class.md)呼び出して[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)します。 それ以外の場合、関数、 [COleException](../../mfc/reference/coleexception-class.md)呼び出して[AfxThrowOleException](exception-processing.md#afxthrowoleexception)します。

この関数は、アプリケーションで OLE 関数の呼び出しの戻り値を確認して使用できます。 アプリケーションでこの関数で戻り値をテストして、最小限のコードでエラー状態に対応できます。

> [!NOTE]
>  この関数では、同じ効果をデバッグし、非デバッグ ビルドします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory

この関数は、空きメモリ プールを検証し、必要に応じて、エラー メッセージを出力します。

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>戻り値

メモリ エラーがない場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

関数にメモリの破損が検出されない場合は、何も出力します。

によって割り当てられたものも含め、ヒープに現在割り当てられているすべてのメモリ ブロックがチェックされます**新しい**などの直接の呼び出しを基になるメモリ アロケーターによって割り当てられたものではありませんが、 **malloc**関数または`GlobalAlloc` Windows 関数。 任意のブロックが壊れている可能性が見つかると、デバッガーの出力メッセージが印刷されます。

行を追加する場合

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

プログラム モジュールの場合、後続の呼び出しで`AfxCheckMemory`メモリが割り当てられたファイル名と行番号が表示されます。

> [!NOTE]
>  モジュールには、シリアル化可能なクラスの 1 つまたは複数の実装が含まれるかどうかは、配置する必要があります、 `#define` IMPLEMENT_SERIAL マクロの最後の呼び出し後の行。

この関数は、MFC のデバッグ バージョンでのみ動作します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxdump"></a>  AfxDump (MFC)

デバッグ中に、オブジェクトの状態をダンプするデバッガーでは、この関数を呼び出します。

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>パラメーター

*私書箱*<br/>
派生したクラスのオブジェクトへのポインター`CObject`します。

### <a name="remarks"></a>Remarks

`AfxDump` オブジェクトの呼び出し`Dump`メンバー関数を指定した場所に情報の送信、`afxDump`変数。 `AfxDump` MFC のデバッグ バージョンでのみ使用できます。

プログラム コードは呼び出さないでください`AfxDump`、代わりに呼び出す必要がありますが、`Dump`適切なオブジェクトのメンバー関数。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

### <a name="see-also"></a>関連項目

[CObject::Dump](cobject-class.md#dump)

##  <a name="afxdumpstack"></a>  AfxDumpStack

現在のスタックのイメージを生成するこのグローバル関数を使用できます。

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>パラメーター

*dwTarget*<br/>
ダンプの出力のターゲットを示します。 可能な値は、ビットごとの OR を使用して結合できます ( **&#124;**) 演算子は、次のとおり。

- AFX_STACK_DUMP_TARGET_TRACE 送信の出力によって、[トレース](#trace)マクロ。 TRACE マクロは、デバッグ ビルドのみで出力を生成します出力を生成しますないリリース ビルドにします。 また、トレースは、デバッガー以外のターゲットにリダイレクトできます。

- 既定のターゲットの出力をダンプ AFX_STACK_DUMP_TARGET_DEFAULT を送信します。 デバッグ ビルドでは、出力は、トレース マクロに移動します。 リリース ビルドでは、出力はクリップボードに移動します。

- AFX_STACK_DUMP_TARGET_CLIPBOARD のみクリップボードに出力を送信します。 データは、エディット クリップボード形式を使用してプレーン テキストとしてクリップボードに配置されます。

- AFX_STACK_DUMP_TARGET_BOTH では、出力をクリップボードにおよび、トレース マクロを同時に送信します。

- Win32 関数を使用して、デバッガーに直接出力の出力が送信`OutputDebugString()`します。 このオプションでは、両方のデバッグでデバッガーの出力を生成し、リリース ビルドのプロセスにデバッガーがアタッチされている場合。 (アタッチされている場合に出力がデバッガーに常に達すると、リダイレクトすることはできません。

### <a name="remarks"></a>Remarks

次の例は、呼び出しから生成された出力を 1 行を反映`AfxDumpStack`MFC ダイアログ アプリケーションのボタン ハンドラーから。

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

上記の出力の各行では、最後の関数呼び出しを関数呼び出しと呼ばれる関数のプロトタイプを含むモジュールの完全なパス名のアドレスを示します。 関数の正確なアドレスで、スタック上で、関数呼び出しが発生しない場合は、バイトのオフセットが表示されます。

たとえば、次の表では、上記の出力の最初の行について説明します。

|出力|説明|
|------------|-----------------|
|`00427D55:`|最後の関数呼び出しの戻りアドレス。|
|`DUMP2\DEBUG\DUMP2.EXE!`|関数呼び出しを含むモジュールの完全なパス名。|
|`void AfxDumpStack(unsigned long)`|関数プロトタイプと呼ばれます。|
|`+ 181 bytes`|関数プロトタイプのアドレスからのバイト オフセット (この場合、 `void AfxDumpStack(unsigned long)`)、リターン アドレスを (この場合、 `00427D55`)。|

`AfxDumpStack` MFC ライブラリのデバッグおよび非デバッグ バージョンで使用できます。ただし、実行可能ファイルが共有 DLL で MFC を使用している場合でも、関数が静的にリンク常にされます。 共有ライブラリの実装では、関数は mfcs42 します。LIB ライブラリ (とそのバリエーション)。

この関数を正常に使用するには。

- IMAGEHLP ファイル。DLL は、パスにある必要があります。 この DLL がない、関数により、エラー メッセージが表示されます。 参照してください[イメージ ヘルプ ライブラリ](/windows/desktop/Debug/image-help-library)IMAGEHLP によって提供される関数のセットについてはします。

- スタック フレームがモジュールには、デバッグ情報を含める必要があります。 デバッグ情報を含んでいない、スタック トレースでは、関数によって生成されますが、トレースがあまり詳しく説明。
  ### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxenablememoryleakdump"></a>  AfxEnableMemoryLeakDump

有効にし、AFX_DEBUG_STATE デストラクターでメモリ リーク ダンプを無効にします。

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>パラメーター

*データファイル*<br/>
[in]TRUE は、メモリ リーク ダンプが有効なことを示しますFALSE は、メモリ リーク ダンプが無効になっていることを示します。

### <a name="return-value"></a>戻り値

このフラグの以前の値。

### <a name="remarks"></a>Remarks

アプリケーションが MFC ライブラリをアンロードしたときに、MFC ライブラリがメモリ リークを確認します。 を介してユーザーにメモリ リークを報告するこの時点で、**デバッグ**Visual Studio のウィンドウ。

アプリケーションが MFC ライブラリの前に別のライブラリを読み込んだ場合、そのライブラリ内の一部のメモリ割り当てが誤ってメモリ リークとして報告されます。 誤ったメモリ リークが原因で、MFC ライブラリがそれらを報告したときに、アプリケーションがゆっくりと終了する可能性があります。 このような場合、 `AfxEnableMemoryLeakDump` を使用してメモリ リーク ダンプを無効にします。

> [!NOTE]
>  この方法を使用してメモリ リーク ダンプをオフにすると、アプリケーションで有効なメモリ リークのレポートを受け取らなくなります。 この方法を使用するのは、メモリ リーク ダンプに誤ったメモリ リークが含まれているという確信がある場合のみにする必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking

MFC のデバッグ バージョンでは、診断メモリ追跡を有効通常。

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>パラメーター

*bTrack*<br/>
この値を TRUE になりますを追跡、メモリの設定FALSE は、オフにします。

### <a name="return-value"></a>戻り値

追跡の有効化フラグの以前の設定。

### <a name="remarks"></a>Remarks

ブロックを正しく割り当てていることがわかっているコードのセクションで追跡を無効にするのにには、この関数を使用します。

詳細については`AfxEnableMemoryTracking`を参照してください[MFC アプリケーションのデバッグ](/visualstudio/debugger/mfc-debugging-techniques)します。

> [!NOTE]
>  この関数は、MFC のデバッグ バージョンでのみ動作します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock

テストの診断のバージョンで割り当てられた現在アクティブなメモリ ブロックを表すかどうかを確認するメモリ アドレス**新しい**します。

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>パラメーター

*p*<br/>
テストするメモリ ブロックへのポインター。

*nBytes*<br/>
メモリ ブロックのバイトの長さが含まれています。

*値を返す*<br/>
指す、**長い**整数メモリ ブロックの割り当てのシーケンス番号が格納されるか、現在アクティブなメモリ ブロックを表していない場合は 0 です。

### <a name="return-value"></a>戻り値

メモリ ブロックが現在割り当てられているし、長さが正しい場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

また、元の割り当てられたサイズに対して指定されたサイズを確認します。 割り当て順序番号が返される場合は、関数は 0 以外の値を返す*値を返す*します。 この数が、ブロックが他のすべての基準が割り当てられた注文を表す**新しい**割り当て。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress

プログラムのメモリ領域内に完全に収まっていることを確認する任意のメモリ アドレスをテストします。

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>パラメーター

*lp*<br/>
テストするのにはメモリ アドレスへのポインター。

*nBytes*<br/>
テストするメモリのバイト数が含まれています。

*bReadWrite*<br/>
メモリの両方に対して読み取りと書き込み (TRUE) または (FALSE) を読むだけであるかどうかを指定します。

### <a name="return-value"></a>戻り値

デバッグ ビルドで指定されたメモリ ブロックの場合は 0 以外は完全に含まれる、プログラムのメモリ領域です。それ以外の場合 0 を返します。

非デバッグ ビルドで 0 以外の値*lp*は NULL。 それ以外の場合に 0 です。

### <a name="remarks"></a>Remarks

アドレスは割り当てられたブロックに限定されない**新しい**します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxisvalidstring"></a>  AfxIsValidString

文字列へのポインターが有効かどうかを判断するのにには、この関数を使用します。

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>パラメーター

*lpsz*<br/>
テストへのポインター。

*されて*<br/>
(バイト単位) をテストする文字列の長さを指定します。 値-1 は、null で終わる文字列をすることを示します。

### <a name="return-value"></a>戻り値

指定されたサイズの文字列を指定したポインターが指している場合、0 以外の場合、デバッグ ビルドでそれ以外の場合 0 を返します。

非デバッグ ビルドで 0 以外の値*lpsz*は NULL。 それ以外の場合に 0 です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxsetallochook"></a>  AfxSetAllocHook

各メモリ ブロックが割り当てられる前に、指定された関数の呼び出しができるようにするフックを設定します。

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>パラメーター

*pfnAllocHook*<br/>
呼び出す関数の名前を指定します。 割り当て関数のプロトタイプの「解説」を参照してください。

### <a name="return-value"></a>戻り値

割り当てを許可する場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

Microsoft Foundation Class ライブラリのデバッグ メモリ アロケーターは、メモリの割り当てを監視して、割り当てが許可されているかどうかを制御するユーザーを許可するユーザー定義フック関数を呼び出すことができます。 割り当てフック関数は、次のようにプロトタイプ宣言されて。

**BOOL AFXAPI AllocHook (size_t** `nSize` **、BOOL** `bObject`**長い** `lRequestNumber` **)。**

*nSize*<br/>
提案されたメモリの割り当てのサイズ。

*bObject*<br/>
TRUE の場合は、割り当て、 `CObject`-派生オブジェクト。 それ以外の場合に FALSE。

*lRequestNumber*<br/>
メモリ割り当てのシーケンス番号。

呼び出し規約 AFXAPI は、呼び出し先がスタックからパラメーターを削除する必要があります意味に注意してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses

指定されたイテレーション関数をすべてシリアル化可能な呼び出し`CObject`-アプリケーションのメモリ空間のクラスを派生します。

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>パラメーター

*pfn*<br/>
各クラスに対して呼び出されるように反復関数へのポインター。 関数の引数がへのポインターを`CRuntimeClass`オブジェクトと、呼び出し元が関数に提供する追加のデータへの void ポインター。

*pContext*<br/>
呼び出し元は、イテレーション関数に指定できる省略可能なデータへのポインター。 このポインターは、NULL を指定できます。

### <a name="remarks"></a>Remarks

シリアル化可能な`CObject`-派生クラスは、DECLARE_SERIAL マクロを使用して派生クラス。 渡されるポインター`AfxDoForAllClasses`で*pContext*それが呼び出されるたびに、指定されたイテレーション関数に渡されます。

> [!NOTE]
>  この関数は、MFC のデバッグ バージョンでのみ動作します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects

派生したすべてのオブジェクトの指定されたイテレーション関数を実行します`CObject`で割り当てられたを**新しい**します。

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>パラメーター

*pfn*<br/>
各オブジェクトに対して実行するイテレーション関数へのポインター。 関数の引数がへのポインター、 `CObject` void 関数を呼び出し元が提供する追加のデータへのポインター。

*pContext*<br/>
呼び出し元は、イテレーション関数に指定できる省略可能なデータへのポインター。 このポインターは、NULL を指定できます。

### <a name="remarks"></a>Remarks

スタック、グローバル、または埋め込みオブジェクトは列挙されません。 渡されたポインター`AfxDoForAllObjects`で*pContext*それが呼び出されるたびに、指定されたイテレーション関数に渡されます。

> [!NOTE]
>  この関数は、MFC のデバッグ バージョンでのみ動作します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
