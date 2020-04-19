---
title: TN039:MFC OLE オートメーションの実装
ms.date: 06/28/2018
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
ms.openlocfilehash: e71b3795396aa73135e8dac022182d4371bb19ac
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611244"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039:しかし、MFC/OLE オートメーションの実装

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

## <a name="overview-of-ole-idispatch-interface"></a>OLE の IDispatch インターフェイスの概要

`IDispatch`インターフェイスは、アプリケーションの機能の使用などの Visual BASIC の場合、またはその他の言語などの他のアプリケーションが実行できるメソッドとプロパティにアプリケーションが公開されることを意味します。 このインターフェイスの最も重要な部分は、`IDispatch::Invoke`関数。 MFC は、「ディスパッチ マップ」を使用して実装する`IDispatch::Invoke`します。 ディスパッチ マップ レイアウト上での「形状」の MFC 実装の情報の提供、 `CCmdTarget`-派生クラスを直接、オブジェクトのプロパティを操作またはメンバーを満たすために、オブジェクト内の関数を呼び出すように`IDispatch::Invoke`要求します。

ほとんどの場合、ClassWizard および MFC は、アプリケーション プログラマから OLE オートメーションの詳細のほとんどを非表示に連携します。 プログラマは、アプリケーションに公開する実際の機能に重点を置いて説明し、基盤となるプラミングについて心配する必要はありません。

ただし、バック グラウンドで MFC の実行内容を理解する必要がある場合があります。 この注はフレームワークの割り当て方法を対処**DISPID**メンバー関数とプロパティにします。 サポート技術情報の割り当てアルゴリズムの**DISPID**s は、アプリケーションのオブジェクトの「タイプ ライブラリ」を作成するときなど、Id がわかっている必要がある場合にのみ必要です。

## <a name="mfc-dispid-assignment"></a>MFC の DISPID の割り当て

(オブジェクトなど、コードのプロパティとメソッドの自動化 (Visual Basic のユーザー、たとえば)、エンドユーザーがの実際の名前が表示されますが、automation が有効にShowWindow) の実装`IDispatch::Invoke`実際の名前を受信しません。 最適化のため、受信、 **DISPID**、これは、32 ビット"マジック cookie"メソッドまたはプロパティへのアクセスをについて説明します。 これら**DISPID**から値が返されます、`IDispatch`と呼ばれる別の方法で実装`IDispatch::GetIDsOfNames`します。 オートメーション クライアント アプリケーションが呼び出す`GetIDsOfNames`アクセス、およびそれ以降の呼び出しに対してキャッシュする予定の各メンバーまたはプロパティと`IDispatch::Invoke`します。 これにより、高価な文字列の検索に一度だけ実行あたり、オブジェクトの使用の代わりに 1 回あたり`IDispatch::Invoke`呼び出します。

MFC の決定、 **DISPID**と各メソッドのプロパティは、次の 2 つに基づきます。

- ディスパッチ マップ (1 単位) の先頭からの距離

- 最派生クラス (0 相対) からディスパッチ マップの距離は、

**DISPID**は 2 つの部分に分かれています。 **LOWORD**の**DISPID**最初のコンポーネントでは、ディスパッチ マップの上部からの距離が含まれています。 **HIWORD**最派生クラスからの距離が含まれています。 例:

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

ご覧のように、OLE オートメーション インターフェイスを公開する 2 つのクラスがあります。 その他から派生し、したがって、OLE オートメーションの部分を含む基本クラスの機能を活用してこれらのクラスのいずれか ("x"と"y"ここではプロパティ)。

MFC が生成する**DISPID**の CDispPoint を次のようにクラスします。

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

プロパティは、基底クラスではないため、 **HIWORD**の**DISPID**は常に 0 (CDispPoint の最派生クラスからの距離は 0)。

MFC が生成する**DISPID**の CDisp3DPoint を次のようにクラスします。

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Z プロパティが指定された、 **DISPID**先頭のゼロ**HIWORD** CDisp3DPoint、プロパティを公開するクラスで定義されているためです。 X および Y プロパティは、基底クラスで定義されているため、 **HIWORD**の**DISPID**のため、これらのプロパティが定義されているクラスが 1 つの派生、最派生クラスからの距離では 1 に設定されています。

> [!NOTE]
> **LOWORD**明示的なマップのエントリがある場合でも、マップ内の位置によっては常に決まります**DISPID** (上の情報は次のセクションを参照してください、 **_ID**バージョン、`DISP_PROPERTY`と`DISP_FUNCTION`マクロ)。

## <a name="advanced-mfc-dispatch-map-features"></a>ディスパッチ マップ機能の詳細

このリリースの Visual C には、ClassWizard がサポートされていない追加の機能の数があります。 サポートされて`DISP_FUNCTION`、 `DISP_PROPERTY`、および`DISP_PROPERTY_EX`メソッド、メンバー変数のプロパティ、および取得/設定メンバー関数のプロパティをそれぞれ定義します。 これらの機能は、通常、ほとんどのオートメーション サーバーを作成するために必要なことだけです。

ClassWizard がサポートされているマクロは不十分である場合、次の追加のマクロを使用できます: `DISP_PROPERTY_NOTIFY`、および`DISP_PROPERTY_PARAM`します。

## <a name="disppropertynotify--macro-description"></a>— DISP_PROPERTY_NOTIFY マクロの説明

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszName*<br/>
プロパティの外部名。

*memberName*<br/>
プロパティが格納されているメンバー変数の名前。

*pfnAfterSet*<br/>
プロパティが変更されたときに呼び出すメンバー関数の名前です。

*vtPropType*<br/>
プロパティの型を指定する値。

### <a name="remarks"></a>Remarks

このマクロは、追加の引数を受け入れることを除いてに、DISP_PROPERTY と似ています。 追加の引数*pfnAfterSet、* nothing を返し、パラメーター 'void OnPropertyNotify()' はメンバー関数にする必要があります。 呼び出されます**後**メンバー変数は変更されています。

## <a name="disppropertyparam--macro-description"></a>— DISP_PROPERTY_PARAM マクロの説明

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszName*<br/>
プロパティの外部名。

*memberGet*<br/>
プロパティを取得するために使用するメンバー関数の名前。

*memberSet*<br/>
プロパティを設定するために使用するメンバー関数の名前。

*vtPropType*<br/>
プロパティの型を指定する値。

*vtsParams*<br/>
領域の文字列には、各パラメーターの vts _ が区切られます。

### <a name="remarks"></a>Remarks

はるか DISP_PROPERTY_EX マクロにこのマクロは別々 の Get および Set メンバー関数でアクセスするプロパティを定義します。 ただし、このマクロを使用すると、プロパティのパラメーター リストを指定できます。 これは、他の方法では、インデックス付きまたはパラメーター化されたプロパティを実装する場合に便利です。 パラメーターは常に配置されます最初に、後に、プロパティの新しい値。 例えば:

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

場合は、get および set メンバー関数に相当します。

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID-マクロの説明

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszName*<br/>
プロパティの外部名。

*dispid*<br/>
プロパティまたはメソッドの固定の DISPID。

*pfnGet*<br/>
プロパティを取得するために使用するメンバー関数の名前。

*pfnSet*<br/>
プロパティを設定するために使用するメンバー関数の名前。

*memberName*<br/>
プロパティにマップするメンバー変数の名前

*vtPropType*<br/>
プロパティの型を指定する値。

*vtsParams*<br/>
領域の文字列には、各パラメーターの vts _ が区切られます。

### <a name="remarks"></a>Remarks

これらのマクロでは、指定できる、 **DISPID** mfc によって自動的にではなくいずれかを割り当てます。 その ID は、マクロ名に追加されます。 ただし、同じ名前を持つこれらのマクロの詳細 (例: **DISP_PROPERTY_ID**) 直後に指定されたパラメーターで ID を特定し、 *pszName*パラメーター。 子を参照してください。これらのマクロの詳細については H します。 **_ID**エントリは、ディスパッチ マップの末尾に配置する必要があります。 自動への影響は**DISPID**以外と同じ方法で生成 **_ID**マクロのバージョンは (、 **DISPID**s は位置によって決まります)。 例えば:

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

Dispid は、MFC によって CDisp3DPoint クラスの次のように生成されます。

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

固定を指定する**DISPID**は、既存のディスパッチ インターフェイスへの下位互換性を維持するために、または特定のシステム定義のメソッドやプロパティを実装するために便利です (通常は、負の値によって示される **。DISPID**など、**な**コレクション)。

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>COleClientItem の IDispatch インターフェイスを取得します。

多くのサーバーでは、OLE サーバーの機能と共に、ドキュメント オブジェクト内でオートメーションをサポートします。 直接アクセスする必要が、この automation インターフェイスにアクセスするために、`COleClientItem::m_lpObject`メンバー変数。 次のコードを取得、`IDispatch`インターフェイスから派生したオブジェクトを`COleClientItem`します。 必要に応じてこの機能が見つかった場合は、アプリケーションで次のコードを含めることができます。

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

ディスパッチ インターフェイスから返されたこの関数が直接使用またはにアタッチしでしたが、`COleDispatchDriver`タイプ セーフ アクセス。 直接使用する場合を呼び出すこと確認その`Release`メンバー使用するときに、ポインター (、`COleDispatchDriver`デストラクターは既定)。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
