---
title: 'テクニカルノート 38: MFC-OLE IUnknown の実装'
ms.date: 06/28/2018
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 9ceb903ec38bc0ad7cfdee1c59babd2379422ac3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302355"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>テクニカル ノート 38: MFC/OLE IUnknown の実装

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

OLE 2 の中核は、"OLE コンポーネント オブジェクト モデル (COM: Component Object Model)" です。 COM は、複数のオブジェクトが相互に協調して通信するための基準を定義しています。 この定義には、オブジェクトにメソッドをディスパッチする方法など、"オブジェクト" を外から見たときの詳細が含まれています。 COM にはまた、基底クラスが定義されています。COM 対応のクラスはすべてこのクラスから派生します。 この基底クラスは[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)です。 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)インターフェイスはC++クラスと呼ばれますが、com は、1つの言語に固有ではありません。 C、PASCAL、または com オブジェクトのバイナリレイアウトをサポートするその他の言語で実装できます。

OLE は、 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)から派生したすべてのクラスを "インターフェイス" として参照します。 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)などの "インターフェイス" が実装されていないため、これは重要な違いです。 この "インターフェイス" と呼ばれるクラスは、オブジェクト間の通信プロトコルだけを定義し、その具体的な実装は定義していません。 これは、システムの最大限の柔軟性を確保するためです。 MFC/C++ プログラムの既定の動作は、MFC (Microsoft Foundation Class) によって実装されます。

MFC における[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)の実装について理解するには、まず、このインターフェイスがどのようなものかを理解する必要があります。 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)の簡略化されたバージョンは次のように定義されています。

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> この説明では、必要な呼び出し規約の詳細の一部 (`__stdcall` など) を省略しています。

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)および[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)メンバー関数は、オブジェクトのメモリ管理を制御します。 COM は、参照カウント スキームを使用してオブジェクトを追跡します。 C++ と異なり、オブジェクトが直接参照されることはありません。 COM オブジェクトは、常にポインターを通じて参照されます。 オブジェクトを使用して所有者が終了したときにオブジェクトを解放するために、オブジェクトの[リリース](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)メンバーが呼び出されます (従来C++のオブジェクトに対して実行されるように、operator delete を使用するのではありません)。 参照カウント スキームを使用することで、単一オブジェクトに対する多重参照を管理できます。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)と[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)の実装では、オブジェクトの参照カウントが保持されます。オブジェクトは、参照カウントが0になるまで削除されません。

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)と[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)は、実装の観点からは非常に簡単です。 実装では次の処理を行うだけです。

```cpp
ULONG CMyObj::AddRef()
{
    return ++m_dwRef;
}

ULONG CMyObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}
```

[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))メンバー関数は、もう少し興味深いものです。 メンバー関数だけが[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)と[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)であるオブジェクトを使用するのは非常に興味深いものではなく、オブジェクトが[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)よりも多くの処理を実行するように指示すると便利です。 ここで、 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))が役に立ちます。 QueryInterface を使用すると、1 つのオブジェクトが複数の "インターフェイス" を持つことができます。 これらのインターフェイスは、通常、 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)から派生し、新しいメンバー関数を追加することによって機能を追加します。 COM インターフェイスでは、インターフェイス内でメンバー変数を宣言せず、メンバー関数はすべて純粋仮想として宣言します。 次に例を示します。

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)がある場合に iprintinterface を取得するには、`IID`の`IPrintInterface`を使用して [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) を呼び出します。 `IID` は、インターフェイスを一意に識別する 128 ビットの数値です。 各インターフェイスには、開発者や OLE によって定義された `IID` があります。 *PUnk*が[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)オブジェクトへのポインターである場合、iprintinterface を取得するコードは次のようになります。

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

これは非常に簡単ですが、iprintinterface と[iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)インターフェイスの[両方をサポート](/windows/win32/api/unknwn/nn-unknwn-iunknown)するオブジェクトを実装する方法は簡単ですが、iprintinterface を実装することにより、iprintinterface は iunknown から直接派生するため、 [iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)は自動的にサポートされます。 例:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)と[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)の実装は、上記で実装したものとまったく同じになります。 `CPrintObj::QueryInterface` は次のようになります。

```cpp
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}
```

上のコード例に示すように、インターフェイス ID (IID) が認識された場合はポインターがオブジェクトに返され、認識されない場合はエラーが発生します。 また、 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))が成功した場合は、暗黙的な[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)が返されます。 もちろん、CEditObj::Print も実装する必要があります。 これは、IPrintInterface が[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)インターフェイスから直接派生しているため単純です。 ただし、 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)から派生した2つの異なるインターフェイスをサポートする場合は、次の点を考慮してください。

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

IEditInterface と IPrintInterface の両方をサポートするクラスは、C++ の多重継承を利用する方法も含めて、さまざまな方法で実装できますが、ここではクラスの入れ子を利用する方法を説明します。

```cpp
class CEditPrintObj
{
public:
    CEditPrintObj();

    HRESULT QueryInterface(REFIID iid, void**);
    ULONG AddRef();
    ULONG Release();
    DWORD m_dwRef;

    class CPrintObj : public IPrintInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_printObj;

    class CEditObj : public IEditInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_editObj;
};
```

以下では、上記の実装全体が含まれています。

```cpp
CEditPrintObj::CEditPrintObj()
{
    m_editObj.m_pParent = this;
    m_printObj.m_pParent = this;
}

ULONG CEditPrintObj::AddRef()
{
    return ++m_dwRef;
}

CEditPrintObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}

HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = &m_printObj;
        AddRef();
        return NOERROR;
    }
    else if (iid == IID_IEditInterface)
    {
        *ppvObj = &m_editObj;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

ULONG CEditPrintObj::CEditObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CEditObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}

ULONG CEditPrintObj::CPrintObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CPrintObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)の実装の大部分は、CEditPrintObj:: CEditObj と CEditPrintObj:: CPrintObj のコードを複製するのではなく、CEditPrintObj クラスに配置されていることに注意してください。 これにより、コードのサイズが圧縮され、バグを回避できます。 ここで重要な点は、IUnknown インターフェイスから、オブジェクトがサポートする可能性のあるインターフェイスを取得するために[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))を呼び出すことができることです。これらの各インターフェイスから、同じことを行うことができます。 これは、各インターフェイスから使用できるすべての[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))関数がまったく同じように動作する必要があることを意味します。 これらの埋め込みオブジェクトから "外側のオブジェクト" の実装を呼び出すために、バック ポインター (m_pParent) が使用されています。 m_pParent ポインターは CEditPrintObj コンストラクターで初期化されます。 CEditPrintObj::CPrintObj::PrintObject と CEditPrintObj::CEditObj::EditObject も同様に実装します。 オブジェクトの編集というたった 1 つの機能を追加するために、大きなコードを追加しました。 しかしインターフェイス内にメンバー関数が 1 つだけということはほとんどなく、この例の場合も、EditObject と PrintObject を 1 つのインターフェイスにまとめるのが普通です。

このように単純なシナリオを実現するために、詳細な説明と大きなコードが必要です。 しかし、MFC/OLE クラスという代替方法を使用することで、同じ機能を簡単に実現できます。 MFC 実装では、Windows メッセージのラップに使用されるメッセージ マップに似た方法を使用します。 この機能は、*インターフェイスマップ*と呼ばれ、次のセクションで説明します。

## <a name="mfc-interface-maps"></a>MFC インターフェイス マップ

MFC/OLE には "インターフェイス マップ" の実装が含まれています。この実装は概念や実行方法が、MFC の "メッセージ マップ" や "ディスパッチ マップ" に似ています。 MFC インターフェイス マップには、次の基本機能があります。

- クラスに組み込まれている`CCmdTarget` [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) の標準実装。

- [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)および[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)によって変更された参照カウントのメンテナンス

- [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))のデータドリブン実装

また、インターフェイス マップは、次の拡張機能もサポートしています。

- 集約可能な COM オブジェクトの作成機能

- COM オブジェクトの実装に他の集約オブジェクトを使用する機能

- これらの実装のフックや拡張

集計の詳細については、「[集計](/windows/win32/com/aggregation)」を参照してください。

MFC インターフェイス マップの基点は `CCmdTarget` クラスです。 `CCmdTarget` "has *-a*" 参照カウントと、 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)実装に関連付けられているすべてのメンバー関数 (参照カウントなどが `CCmdTarget`) です。 OLE COM をサポートするクラスを作成するには `CCmdTarget` の派生クラスを作成し、マクロや `CCmdTarget` メンバー関数を利用して必要なインターフェイスを実装します。 MFC 実装では、上の例で示したように各インターフェイスの実装で入れ子になったクラスが使用され、 IUnknown の標準実装によって簡略化されています。また、コード簡略化のために多くのマクロも用意されています。

## <a name="interface-map-basics"></a>インターフェイス マップの基本

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>MFC インターフェイス マップを利用したクラスを作成するには

1. `CCmdTarget` クラスの直接派生クラスまたは間接派生クラスを作成します。

2. 派生クラスで関数 `DECLARE_INTERFACE_MAP` を定義します。

3. サポートする各インターフェイスに対して、クラス定義で BEGIN_INTERFACE_PART および END_INTERFACE_PART マクロを使用します。

4. 実装ファイルで、BEGIN_INTERFACE_MAP と END_INTERFACE_MAP マクロを使用して、クラスのインターフェイスマップを定義します。

5. サポートされている各 IID に対して、BEGIN_INTERFACE_MAP と END_INTERFACE_MAP マクロの間に INTERFACE_PART マクロを使用して、その IID をクラスの特定の "部分" にマップします。

6. 入れ子になったクラスとして、サポートするインターフェイスを実装します。

7. METHOD_PROLOGUE マクロを使用して、親の `CCmdTarget`派生オブジェクトにアクセスします。

8. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)、および[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))は、これらの関数の `CCmdTarget` 実装 (`ExternalAddRef`、`ExternalRelease`、および `ExternalQueryInterface`) に委任できます。

上の例の CPrintEditObj の場合は次のように実装できます。

```cpp
class CPrintEditObj : public CCmdTarget
{
public:
    // member data and member functions for CPrintEditObj go here

// Interface Maps
protected:
    DECLARE_INTERFACE_MAP()

    BEGIN_INTERFACE_PART(EditObj, IEditInterface)
        STDMETHOD_(void, EditObject)();
    END_INTERFACE_PART(EditObj)

    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)
        STDMETHOD_(void, PrintObject)();
    END_INTERFACE_PART(PrintObj)
};
```

この宣言によって `CCmdTarget` 派生クラスが作成されます。 DECLARE_INTERFACE_MAP マクロは、このクラスがカスタムインターフェイスマップを持つことをフレームワークに指示します。 さらに、BEGIN_INTERFACE_PART および END_INTERFACE_PART のマクロでは、入れ子になったクラスを定義します。この例では、CEditObj と CPrintObj という名前を使用しています (X は、"C" で始まるグローバルクラスと入れ子になったクラスを区別するためにのみ使用されます。"I" で開始します)。 これらの入れ子になった 2 つのクラスのそれぞれに、入れ子になった 2 つのメンバー m_CEditObj と m_CPrintObj が作成されます。 これらのマクロは、自動的に[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)、および[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))関数を宣言します。したがって、このインターフェイスに固有の関数 (EditObject と PrintObject) のみを宣言します (OLE マクロ STDMETHOD を使用して、ターゲットプラットフォームに対して **_stdcall**と仮想キーワードが適切に提供されるようにします)。

このクラスに対するインターフェイス マップを実装するには:

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

これにより IID_IPrintInterface IID と m_CPrintObj、IID_IEditInterface IID と m_CEditObj が関連付けられます。 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) (`CCmdTarget::ExternalQueryInterface`) の `CCmdTarget` 実装では、このマップを使用して、要求されたときに m_CPrintObj および m_CEditObj へのポインターを返します。 `IID_IUnknown` に対するエントリをマップに含める必要はありません。`IID_IUnknown` が要求されると、マップの先頭のインターフェイス (この場合は m_CPrintObj) が使用されます。

BEGIN_INTERFACE_PART マクロによって自動的に[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 、 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))関数が宣言されていても、それを実装する必要があります。

```cpp
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalAddRef();
}

ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalRelease();
}

HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);
}

void FAR EXPORT CEditPrintObj::XEditObj::EditObject()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    // code to "Edit" the object, whatever that means...
}
```

CEditPrintObj::CPrintObj の実装は、上の CEditPrintObj::CEditObj の定義に似ています。 ここに示した関数を自動的に生成するマクロを作成することも可能ですが (開発初期バージョンの MFC/OLE では実際に作成されていました)、マクロが複数行に展開される場合はブレークポイントの設定が難しくなります。 このため、コードは手動で展開されます。

フレームワーク実装のメッセージ マップを利用すると、次の作業が不要になります。

- QueryInterface の実装

- AddRef と Release の実装

- 各インターフェイスに対するこれらの組み込みメソッドの宣言

フレームワーク内部でもメッセージ マップが使用されています。 このため、フレームワーク クラス (`COleServerDoc` など) の派生クラスを作成すると、そのクラスは自動的に数種類のインターフェイスを持つことになります。また、このインターフェイスを変更したり、まったく新しいインターフェイスに置き換えたりすることもできます。 これは、フレームワークが基底クラスからのインターフェイス マップの継承を完全にサポートしているためです。 これは、BEGIN_INTERFACE_MAP が2番目のパラメーターとして、基底クラスの名前を受け取る理由です。

> [!NOTE]
> 通常は、MFC から埋め込みに特殊化したインターフェイスを継承しても、MFC の組み込み OLE インターフェイスの実装を再利用できません。 これはできません。これは、METHOD_PROLOGUE マクロを使用して、含まれている `CCmdTarget`派生オブジェクトにアクセスする場合、`CCmdTarget`派生オブジェクトからの埋め込みオブジェクトの*固定オフセット*を意味するためです。 たとえば `COleClientItem::XAdviseSink` では、MFC 実装から埋め込みの XMyAdviseSink を派生できません。これは XAdviseSink では、`COleClientItem` オブジェクトの先頭からのオフセット値が異なる値になるためです。

> [!NOTE]
> ただし、これらの関数に MFC の既定の動作を求めるときは、MFC 実装に処理を任せることができます。 これは `IOleInPlaceFrame` クラスで MFC 実装の `COleFrameHook` (XOleInPlaceFrame) によって行われます。このクラスは多くの関数に対して m_xOleInPlaceUIWindow に処理を任せます。 この設計は、多数のインターフェイスを含むオブジェクトの実行時サイズを小さくする目的で選択されます。この処理ではバック ポインター (前の m_pParent など) は不要です。

### <a name="aggregation-and-interface-maps"></a>集約とインターフェイス マップ

MFC はスタンドアロンの COM オブジェクトのほかに、集約もサポートしています。 ここでは、集計自体が複雑すぎてトピックを説明しています。集計の詳細については、[集計](/windows/win32/com/aggregation)のトピックを参照してください。 ここではフレームワークとインターフェイス マップに組み込まれている集約に限定して説明します。

集約の利用方法には、(1) 集約をサポートする COM オブジェクトの利用、(2) 集約の一部となることができるオブジェクトの作成の 2 種類があります。 これらの機能はそれぞれ "集約オブジェクトの利用" と "集約可能オブジェクトの作成" と呼ばれます。 MFC ではこの両方がサポートされています。

### <a name="using-an-aggregate-object"></a>集約オブジェクトの利用

集約オブジェクトを使用するには、集約を QueryInterface 機構に結び付ける必要があります。 つまり、本体オブジェクトに最初から含まれているかのように集約オブジェクトを動作させる必要があります。 これは、入れ子になったオブジェクトが IID にマップされる INTERFACE_PART マクロに加えて、MFC のインターフェイスマップ機構とどのように関連付けられているのか、`CCmdTarget` 派生クラスの一部として集計オブジェクトを宣言することもできます。 これを行うには、INTERFACE_AGGREGATE マクロを使用します。 これにより、インターフェイスマップ機構に統合されるメンバー変数 ( [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)または派生クラスへのポインターである必要があります) を指定できます。 が呼び出されたときに`CCmdTarget::ExternalQueryInterface`ポインターが NULL でない場合、 `IID`要求されたがによっ`IID` `CCmdTarget`てサポートされるネイティブのではない場合、フレームワークは、集計オブジェクトの [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) メンバー関数を自動的に呼び出します。オブジェクト自体。

#### <a name="to-use-the-interface_aggregate-macro"></a>マクロ INTERFACE_AGGREGATE を使用するには

1. 集約オブジェクトへのポインター (`IUnknown*`) となるメンバー変数を宣言します。

2. インターフェイスマップに INTERFACE_AGGREGATE マクロを含めます。このマクロは、名前でメンバー変数を参照します。

3. 適切な時点で (普通は `CCmdTarget::OnCreateAggregates` 内) このメンバー変数を NULL 値以外の値に初期化します。

例:

```cpp
class CAggrExample : public CCmdTarget
{
public:
    CAggrExample();

protected:
    LPUNKNOWN m_lpAggrInner;
    virtual BOOL OnCreateAggregates();

    DECLARE_INTERFACE_MAP()
    // "native" interface part macros may be used here
};

CAggrExample::CAggrExample()
{
    m_lpAggrInner = NULL;
}

BOOL CAggrExample::OnCreateAggregates()
{
    // wire up aggregate with correct controlling unknown
    m_lpAggrInner = CoCreateInstance(CLSID_Example,
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)
        return FALSE;
    // optionally, create other aggregate objects here
    return TRUE;
}

BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)
    // native "INTERFACE_PART" entries go here
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)
END_INTERFACE_MAP()
```

m_lpAggrInner 変数はコンストラクターによって NULL に初期化されます。 このフレームワークでは、 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))の既定の実装で NULL メンバー変数が無視されます。 集約オブジェクトは `OnCreateAggregates` で作成するのが適切です。 MFC 実装の `COleObjectFactory` 以外でオブジェクトを作成するときは、この関数を明示的に呼び出します。 `CCmdTarget::OnCreateAggregates` で集約オブジェクトを作成し、`CCmdTarget::GetControllingUnknown` を使用する理由は、集約可能オブジェクトの作成方法を解説する際に説明します。

上の方法を使用すると、オブジェクト本来のインターフェイスに加えて集約オブジェクトが持つすべてのインターフェイスを持つことができます。 集約オブジェクトがサポートするインターフェイスの一部だけを利用するには、`CCmdTarget::GetInterfaceHook` をオーバーライドします。 これにより、 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))に似た、非常に低いレベルの hookability が可能になります。 通常は、集約オブジェクトがサポートするすべてのインターフェイスを使用します。

### <a name="making-an-object-implementation-aggregatable"></a>集約可能なオブジェクト実装のための作業

オブジェクトを集約可能にするには、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)、および[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))の実装が "不明な制御" に委任されている必要があります。 つまり、オブジェクトの一部として使用されるためには、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)、および[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))を別のオブジェクト ( [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)から派生したオブジェクト) に委任する必要があります。 この "controlling unknown" はオブジェクトが作成されるときにオブジェクト対して指定されます。つまり、`COleObjectFactory` の実装に対して指定されることになります。 COleObjectFactory をこのように実装すると、若干のオーバーヘッドが発生するため、場合によっては適切でない場合もあります。このため、MFC ではこの処理はオプションとして選択できるようになっています。 オブジェクトを集約可能にするには、そのオブジェクトのコンストラクターから `CCmdTarget::EnableAggregation` を呼び出します。

オブジェクトで集約を使用するときは、適切な "controlling unknown" が集約オブジェクトに渡されるようにする必要があります。 通常、この[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)ポインターは、集計が作成されるときにオブジェクトに渡されます。 たとえば、`CoCreateInstance` を使用してオブジェクトを作成すると、パラメーター pUnkOuter が "controlling unknown" になります。 正確な "controlling unknown" ポインターは、`CCmdTarget::GetControllingUnknown` を呼び出して取得できます。 しかし、コンストラクター中ではこの関数の戻り値は保証されません。 このため、集約オブジェクトは `CCmdTarget::OnCreateAggregates` をオーバーライドした関数の中でのみ作成することを推奨します。この中では (`GetControllingUnknown` 実装から作成されたものであっても) `COleObjectFactory` の戻り値は保証されます。

架空の参照カウントを作成または解放するときに、オブジェクトが正しい参照カウントを操作することも重要です。 これを保証するために、`ExternalAddRef` と `ExternalRelease` ではなく、必ず `InternalRelease` と `InternalAddRef` を呼び出すようにしてください。 集約をサポートするクラスで `InternalRelease` と `InternalAddRef` を呼び出すことはほとんどありません。

## <a name="reference-material"></a>リファレンス マニュアル

独自のインターフェイスの定義や、フレームワークの OLE インターフェイスのオーバーライドなど、OLE の高度な機能を利用するときは、基盤となるインターフェイス マップ機構の使い方を理解しておく必要があります。

ここでは、このような高度な機能の実装に使用されるマクロと API について説明します。

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation - 関数の説明

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>コメント

この種のオブジェクトについて OLE 集約をサポートする場合、この関数を派生クラスのコンストラクターで呼び出します。 この関数を呼び出すことによって、集約可能オブジェクトに必要な特別な IUnknown 実装が用意されます。

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface — 関数の説明

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>パラメーター

*lpIID*<br/>
IID への far ポインター (QueryInterface の第 1 引数)

*ppvObj*<br/>
IUnknown* へのポインター (QueryInterface の第 2 引数)

#### <a name="remarks"></a>コメント

IUnknown を実装するとき、クラスが実装する各インターフェイスに対してこの関数を呼び出します。 この関数はオブジェクトのインターフェイス マップに基づき、標準的なデータ駆動型の QueryInterface を実行します。 この関数の戻り値は HRESULT 型にキャストする必要があります。 集約オブジェクトの場合、この関数はローカルなインターフェイス マップを使用せずに、"controlling IUnknown" を呼び出します。

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef - 関数の説明

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>コメント

IUnknown::AddRef を実装するとき、クラスが実装する各インターフェイスに対してこの関数を呼び出します。 戻り値は、CCmdTarget オブジェクトの新しい参照カウント値を示します。 集約オブジェクトの場合、この関数はローカルな参照カウントを操作せずに、"controlling IUnknown" を呼び出します。

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease - 関数の説明

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>コメント

IUnknown::Release を実装するとき、クラスが実装する各インターフェイスに対してこの関数を呼び出します。 戻り値は、オブジェクトの新しい参照カウント値を示します。 集約オブジェクトの場合、この関数はローカルな参照カウントを操作せずに、"controlling IUnknown" を呼び出します。

### <a name="declare_interface_map--macro-description"></a>DECLARE_INTERFACE_MAP - マクロの説明

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>コメント

このマクロは、`CCmdTarget` からの派生クラスのうち、インターフェイス マップを持つすべてのクラスで使用します。 DECLARE_MESSAGE_MAP とほとんど同じ方法で使用されます。 このマクロ呼び出しは、クラス定義 (通常はヘッダー (.H) ファイル内) で使用します。 DECLARE_INTERFACE_MAP を持つクラスは、実装ファイル () でインターフェイスマップを定義する必要があります。CPP) を BEGIN_INTERFACE_MAP し、END_INTERFACE_MAP マクロを使用します。

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>BEGIN_INTERFACE_PART、END_INTERFACE_PART - マクロの説明

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>パラメーター

*localClass*<br/>
このインターフェイスを実装するクラスの名前

*iface*<br/>
このクラスによって実装されるインターフェイスの名前

#### <a name="remarks"></a>コメント

クラスが実装する各インターフェイスに対して、BEGIN_INTERFACE_PART と END_INTERFACE_PART のペアを持っている必要があります。 これらのマクロでは、OLE インターフェイスから派生させるローカル クラスと、そのクラスの埋め込みメンバー変数を定義します。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)、および[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))メンバーは、自動的に宣言されます。 実装するインターフェイスの一部である他のメンバー関数の宣言を含める必要があります (これらの宣言は、BEGIN_INTERFACE_PART と END_INTERFACE_PART マクロの間に配置されます)。

*Iface*引数は、`IAdviseSink`、`IPersistStorage` (または独自のカスタムインターフェイス) など、実装する OLE インターフェイスです。

*Localclass*引数は、定義されるローカルクラスの名前です。 名前の先頭には 'X' が自動的に付けられます。 この名前付け規則は、グローバル クラス名との競合を回避するためです。 また、埋め込みメンバーの名前は、' m_x ' で始まることを除いて、 *Localclass*名と同じになります。

例:

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

これによって IAdviseSink から派生されるローカル クラス XMyAdviseSink が定義されます。またこのクラスのメンバー名は m_xMyAdviseSink になります。

> [!NOTE]
> `STDMETHOD`_ で始まる行は、OLE2 から基本的にコピーされます。H とを少し変更しました。 OLE2.H からコピーすると、発見が困難なエラーを回避できます。

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>BEGIN_INTERFACE_MAP、END_INTERFACE_MAP - マクロの説明

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>パラメーター

*クラス*<br/>
定義するインターフェイス マップが含まれるクラス

*baseClass*<br/>
*クラス*の派生元のクラス。

#### <a name="remarks"></a>コメント

実装ファイルでは、BEGIN_INTERFACE_MAP マクロと END_INTERFACE_MAP マクロを使用して、インターフェイスマップを実際に定義します。 実装される各インターフェイスには、1つ以上の INTERFACE_PART マクロの呼び出しがあります。 クラスで使用される集計ごとに、1つのマクロ呼び出し INTERFACE_AGGREGATE ます。

### <a name="interface_part--macro-description"></a>INTERFACE_PART - マクロの説明

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>パラメーター

*クラス*<br/>
インターフェイス マップを持つクラスの名前。

*iid*<br/>
埋め込みクラスに割り当てられる `IID`。

*localClass*<br/>
ローカル クラスの名前。'X' は付けません。

#### <a name="remarks"></a>コメント

このマクロは、オブジェクトがサポートする各インターフェイスの BEGIN_INTERFACE_MAP マクロと END_INTERFACE_MAP マクロの間で使用されます。 これにより、*クラス*および*localclass*によって示されるクラスのメンバーに IID をマップできます。 ' M_x ' が*Localclass*に自動的に追加されます。 1 個のメンバーに複数の `IID` を割り当てることもできます。 これは、"最派生" インターフェイスを 1 個だけ作成し、これをすべての中間インターフェイスとして使用するときにも役に立ちます。 この方法を使用した例が `IOleInPlaceFrameWindow` インターフェイスです。 このインターフェイスの階層構造は次のようになっています。

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

オブジェクトが `IOleInPlaceFrameWindow`を実装している場合、クライアントは、`IOleUIWindow`、`IOleWindow`、または[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)のいずれのインターフェイスにも `QueryInterface` できます (実際に実装しているインターフェイス `IOleInPlaceFrameWindow`)。 これを処理するには、複数の INTERFACE_PART マクロを使用して、すべての基本インターフェイスを `IOleInPlaceFrameWindow` インターフェイスにマップします。

クラス定義ファイルには次のように記述されます。

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

クラス実装ファイルには次のように記述されます。

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

IUnknown は常に必要であるため、フレームワークによって自動的にサポートされます。

### <a name="interface_part--macro-description"></a>INTERFACE_PART - マクロの説明

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>パラメーター

*クラス*<br/>
インターフェイス マップを持つクラスの名前。

*theAggr*<br/>
集約するメンバー変数の名前。

#### <a name="remarks"></a>コメント

このマクロは、クラスが集約オブジェクトを使用することをフレームワークに知らせます。 BEGIN_INTERFACE_PART と END_INTERFACE_PART のマクロの間に表示される必要があります。 集計オブジェクトは、 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)から派生した独立したオブジェクトです。 集計と INTERFACE_AGGREGATE マクロを使用することにより、集約でサポートされているすべてのインターフェイスが、オブジェクトによって直接サポートされていると思われるようにすることができます。 *Theaggr*引数は、 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)から派生したクラスのメンバー変数の名前です (直接または間接的)。 すべての INTERFACE_AGGREGATE マクロは、インターフェイスマップに配置するときに INTERFACE_PART マクロに従う必要があります。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
