---
title: テクニカル ノート 65:OLE オートメーションサーバーのデュアルインターフェイスサポート
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 1508b5219f7bb7fd2e9c9a56c42c30bb99686804
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630392"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>テクニカル ノート 65:OLE オートメーションサーバーのデュアルインターフェイスサポート

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このメモでは、MFC ベースの OLE オートメーションサーバーアプリケーションにデュアルインターフェイスサポートを追加する方法について説明します。 [Acdual](../overview/visual-cpp-samples.md)サンプルは、デュアルインターフェイスのサポートを示しています。このメモのコード例は、acdual から取得されています。 このメモに記載されているマクロ (DECLARE_DUAL_ERRORINFO、DUAL_ERRORINFO_PART、IMPLEMENT_DUAL_ERRORINFO など) は、ACDUAL のサンプルに含まれており、MFCDUAL で見つかります。始め.

## <a name="dual-interfaces"></a>デュアルインターフェイス

Ole オートメーションでは、 `IDispatch`インターフェイス、VTBL インターフェイス、またはデュアルインターフェイス (両方を含む) を実装することができますが、公開されているすべての OLE オートメーションオブジェクトに対してデュアルインターフェイスを実装することを強くお勧めします。 デュアルインターフェイスには、また`IDispatch`は VTBL 専用のインターフェイスよりも大きな利点があります。

- バインディングは、コンパイル時に VTBL インターフェイスまたは実行時`IDispatch`に実行されます。

- VTBL インターフェイスを使用できる OLE オートメーションコントローラーは、パフォーマンスの向上によってメリットが得られる場合があります。

- インターフェイスを使用する既存の OLE `IDispatch`オートメーションコントローラーは、引き続き機能します。

- VTBL インターフェイスは、からC++より簡単に呼び出すことができます。

- Visual Basic オブジェクトサポート機能との互換性を確保するには、デュアルインターフェイスが必要です。

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>CCmdTarget ベースのクラスへのデュアルインターフェイスサポートの追加

デュアルインターフェイスは、から`IDispatch`派生したカスタムインターフェイスにすぎません。 ベースのクラスで`CCmdTarget`デュアルインターフェイスサポートを実装する最も簡単な方法は、最初に MFC と ClassWizard を使用してクラスに通常のディスパッチインターフェイスを実装してから、後でカスタムインターフェイスを追加することです。 ほとんどの場合、カスタムインターフェイスの実装は、単純に MFC `IDispatch`実装に戻ります。

まず、サーバーの ODL ファイルを変更して、オブジェクトのデュアルインターフェイスを定義します。 デュアルインターフェイスを定義するには、Visual `DISPINTERFACE` C++ wizard が生成するステートメントではなく、インターフェイスステートメントを使用する必要があります。 既存`DISPINTERFACE`のステートメントを削除するのではなく、新しい interface ステートメントを追加します。 `DISPINTERFACE`フォームを保持することで、引き続き ClassWizard を使用してオブジェクトにプロパティとメソッドを追加できますが、インターフェイスステートメントには、同等のプロパティとメソッドを追加する必要があります。

デュアルインターフェイスのインターフェイスステートメントには、 *OLEAUTOMATION*および*dual*属性が含まれている必要があり、インターフェイス`IDispatch`はから派生する必要があります。 [Guidgen.exe](../overview/visual-cpp-samples.md)サンプルを使用して、デュアルインターフェイスの**IID**を作成できます。

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Interface ステートメントを配置したら、メソッドとプロパティのエントリを追加します。 デュアルインターフェイスの場合は、パラメーターリストを再配置して、デュアルインターフェイスのメソッドとプロパティアクセサー関数が**HRESULT**を返し、その戻り値をパラメーターとして属性`[retval,out]`として渡すようにする必要があります。 プロパティについては、read (`propget`) アクセス関数と write (`propput`) アクセス関数の両方を同じ id で追加する必要があることに注意してください。例えば:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

メソッドとプロパティを定義したら、コクラスステートメントで interface ステートメントへの参照を追加する必要があります。 例えば:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

ODL ファイルが更新されたら、mfc のインターフェイスマップ機構を使用して、オブジェクトクラスのデュアルインターフェイスの実装クラスを定義し、対応するエントリを mfc `QueryInterface`の機構で作成します。 ODL の interface ステートメントの各`INTERFACE_PART`エントリに対して、ブロック内に1つのエントリと、ディスパッチインターフェイスのエントリが必要です。 *Propput*属性を持つ各 ODL エントリには、と`put_propertyname`いう名前の関数が必要です。 *Propget*属性を持つ各エントリには、と`get_propertyname`いう名前の関数が必要です。

デュアルインターフェイスの実装クラスを定義するには、オブジェクト`DUAL_INTERFACE_PART`クラス定義にブロックを追加します。 例えば:

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

デュアルインターフェイスを MFC の[QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object)機構に接続するには、 `INTERFACE_PART`インターフェイスマップにエントリを追加します。

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

次に、インターフェイスの実装に入力する必要があります。 ほとんどの場合、既存の MFC `IDispatch`実装に委任することができます。 例えば:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

オブジェクトのメソッドとプロパティアクセサー関数の場合は、実装に入力する必要があります。 通常、メソッドとプロパティ関数は、ClassWizard を使用して生成されたメソッドにデリゲートを返すことができます。 ただし、変数に直接アクセスするためのプロパティを設定する場合は、変数に値を取得/配置するコードを記述する必要があります。 例えば:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>デュアルインターフェイスポインターを渡す

デュアルインターフェイスポインターを渡すことは、特にを呼び出す`CCmdTarget::FromIDispatch`必要がある場合は、簡単ではありません。 `FromIDispatch`は、MFC の`IDispatch`ポインターに対してのみ機能します。 これを回避する方法の1つとして、 `IDispatch` MFC によって設定された元のポインターを照会し、それを必要とする関数にそのポインターを渡す方法があります。 例えば:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

デュアルインターフェイスメソッドを使用してポインターを戻す前に、MFC `IDispatch`ポインターからデュアルインターフェイスポインターに変換することが必要になる場合があります。 例えば:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>アプリケーションのタイプライブラリを登録しています

AppWizard は、OLE オートメーションサーバーアプリケーションのタイプライブラリをシステムに登録するコードを生成しません。 タイプライブラリを登録する方法は他にもありますが、アプリケーションが OLE 型情報を更新するときにタイプライブラリを登録すると便利です。つまり、アプリケーションがスタンドアロンで実行されるときには、そのタイプライブラリを登録すると便利です。

アプリケーションがスタンドアロンで実行されるときに、アプリケーションのタイプライブラリを登録するには、次のようにします。

- AFXCTL.H を含めます。標準の H には、ヘッダーファイル STDAFX.H が含まれています。H `AfxOleRegisterTypeLib`関数の定義にアクセスするために使用します。

- アプリケーションの`InitInstance`関数で、へ`COleObjectFactory::UpdateRegistryAll`の呼び出しを見つけます。 この呼び出しの後に、タイプライブラリ`AfxOleRegisterTypeLib`に対応する**LIBID**と、タイプライブラリの名前を指定して、への呼び出しを追加します。

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>タイプライブラリの変更に対応するようにプロジェクトのビルド設定を変更する

タイプライブラリが再構築されるたびに、 **UUID**定義を含むヘッダーファイルが MkTypLib によって生成されるように、プロジェクトのビルド設定を変更するには、次のようにします。

1. **ビルド** メニューの **設定** をクリックし、各構成の ファイル ボックスの一覧から ODL ファイルを選択します。

2. **[OLE の種類]** タブをクリックし、 **[出力ヘッダー]** ファイル名 フィールドにファイル名を指定します。 MkTypLib によって既存のファイルが上書きされるので、プロジェクトで使用されていないファイル名を使用します。 [ **OK]** をクリックして、 **[ビルドの設定]** ダイアログボックスを閉じます。

MkTypLib によって生成されたヘッダーファイルからプロジェクトに**UUID**定義を追加するには、次のようにします。

1. MkTypLib によって生成されるヘッダーファイルを標準のヘッダーファイル*stdafx.h*にインクルードします。

2. 新しいファイル INITIIDS を作成します。CPP を使用し、プロジェクトに追加します。 このファイルには、OLE2 を含めた後に、MkTypLib で生成されたヘッダーファイルを含めます。H と INITGUID。始め

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. **ビルド** メニューの **設定** をクリックし、initiids を選択します。各構成のファイルリストからの CPP。

4. **C++** タブをクリックし、Category **[プリコンパイル済みヘッダー]** をクリックして、 **[プリコンパイル済みヘッダーを使用しない]** オプションボタンを選択します。 OK をクリックして、**ビルドの設定** ダイアログボックスを閉じます。

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>タイプライブラリでの正しいオブジェクトクラス名の指定

ビジュアルC++に付属しているウィザードでは、実装クラス名を使用して、OLE 作成可能なクラスのサーバーの ODL ファイルにコクラスを指定します。 これは機能しますが、実装クラス名は、オブジェクトのユーザーが使用するクラス名ではない場合があります。 正しい名前を指定するには、ODL ファイルを開き、各コクラスステートメントを見つけて、実装クラス名を正しい外部名に置き換えます。

Coclass ステートメントが変更されると、MkTypLib によって生成されるヘッダーファイル内の**CLSID**の変数名がそれに応じて変更されることに注意してください。 新しい変数名を使用するには、コードを更新する必要があります。

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>例外とオートメーションエラーインターフェイスの処理

オートメーションオブジェクトのメソッドとプロパティアクセサー関数は、例外をスローする場合があります。 その場合は、それらをデュアルインターフェイスの実装で処理し、例外に関する情報を OLE オートメーションのエラー処理インターフェイス () `IErrorInfo`を使用してコントローラーに渡す必要があります。 このインターフェイスは、および VTBL インターフェイスの両方`IDispatch`を介して、詳細なコンテキストエラー情報を提供します。 エラーハンドラーが使用可能であることを示すには、 `ISupportErrorInfo`インターフェイスを実装する必要があります。

エラー処理機構を示すために、標準ディスパッチサポートを実装するために使用される ClassWizard で生成された関数が例外をスローするとします。 MFC のの実装`IDispatch::Invoke`では、通常、これらの例外をキャッチし、 `Invoke`呼び出しによって返される EXCEPTINFO 構造体に変換します。 ただし、VTBL インターフェイスを使用する場合は、自分で例外をキャッチする必要があります。 デュアルインターフェイスのメソッドを保護する例を次に示します。

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL`は、例外が発生したときに正しいエラーコードを返すようにします。 `CATCH_ALL_DUAL`インターフェイスを使用して、 `ICreateErrorInfo` MFC 例外を OLE オートメーションエラー処理情報に変換します。 (例`CATCH_ALL_DUAL`のマクロは、mfcdual というファイルにあります。「 [ACDUAL](../overview/visual-cpp-samples.md)サンプルの H」。 例外を`DualHandleException`処理するために呼び出す関数は、ファイルの mfcdual にあります。CPP)`CATCH_ALL_DUAL`発生した例外の種類に基づいて返されるエラーコードを決定します。

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) -この場合、 `HRESULT`は次のコードを使用して構築されます。

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   これにより`HRESULT` 、例外の原因となったインターフェイスに固有のが作成されます。 エラーコードは0x200 によってオフセットされ、標準 OLE インターフェイスの`HRESULT`システム定義のと競合しないようにします。

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) -この場合は、 `E_OUTOFMEMORY`が返されます。

- その他の例外-この場合は`E_UNEXPECTED` 、が返されます。

OLE オートメーションエラーハンドラーが使用されていることを示すには、 `ISupportErrorInfo`インターフェイスも実装する必要があります。

まず、オートメーションクラス定義にコードを追加して、が`ISupportErrorInfo`サポートするようにします。

次に、オートメーションクラスのインターフェイスマップにコードを追加して`ISupportErrorInfo` 、実装クラスを MFC `QueryInterface`の機構に関連付けます。 ステートメント`INTERFACE_PART`は、に対し`ISupportErrorInfo`て定義されているクラスと一致します。

最後に、をサポート`ISupportErrorInfo`するように定義されているクラスを実装します。

( [ACDUAL](../overview/visual-cpp-samples.md)サンプルには、 `DECLARE_DUAL_ERRORINFO`、 `DUAL_ERRORINFO_PART`、および`IMPLEMENT_DUAL_ERRORINFO`の3つの手順を実行するのに役立つ3つのマクロが含まれています。これらはすべて mfcdual に含まれています。H)

次の例では、をサポート`ISupportErrorInfo`するように定義されたクラスを実装しています。 `CAutoClickDoc`はオートメーションクラス`IID_IDualAClick`の名前で、は OLE オートメーション error オブジェクトを介して報告されるエラーのソースであるインターフェイスの**IID**です。

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
