---
title: TN016:MFC での C++ の多重継承の使用
ms.date: 06/28/2018
f1_keywords:
- vc.inheritance
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
ms.openlocfilehash: 76dc2e856ca7db783ee542aa2dbb498fd4c1a769
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306130"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016:MFC での C++ の多重継承の使用

ここでは、Microsoft Foundation Classes を多重継承 (MI) を使用する方法について説明します。 多重継承の使用は、MFC では必要ありません。 MI は、すべての MFC クラスで使用されていないと、クラス ライブラリを作成する必要はありません。

次のサブトピックでは、MI が一般的な MFC の表現方法だけでなく MI の制限のいくつかの使用に与える影響について説明します。 これらの制限の一部は C++ の一般的な制限です。 他のユーザーは、MFC アーキテクチャによって課されます。

このテクニカル ノートの最後には、多重継承を使用する完全な MFC アプリケーションが表示されます。

## <a name="cruntimeclass"></a>CRuntimeClass

永続化と MFC の使用の動的オブジェクトの作成メカニズム、 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)クラスを一意に識別するデータ構造体。 MFC は、これらの構造体のいずれかが、アプリケーションの各動的やシリアル化可能なクラスに関連付けます。 型の場合は、特別な静的オブジェクトを使用して、アプリケーションの起動時にこれらの構造体が初期化される`AFX_CLASSINIT`します。

現在の実装`CRuntimeClass`MI ランタイム型情報をサポートしていません。 これは、MFC アプリケーションで多重継承を使うことはできませんという意味ではありません。 ただし、1 つ以上の基底クラスのオブジェクトを使用する場合は、特定の責任があります。

[使うため](../mfc/reference/cobject-class.md#iskindof)メソッドは正確に判定オブジェクトの型が複数の基底クラス。 そのため、使用することはできません[CObject](../mfc/reference/cobject-class.md)仮想基底クラス、およびすべての呼び出しとして`CObject`などの関数メンバー [cobject::serialize](../mfc/reference/cobject-class.md#serialize)と[CObject::operator 新しい](../mfc/reference/cobject-class.md#operator_new)その C++ は、適切な関数呼び出しを区別できますので、スコープ修飾子をいる必要があります。 プログラムでは、MFC 内で多重継承を使用する場合、クラスを格納している、`CObject`基底クラスを基底クラスの一覧の一番左のクラスである必要があります。

代わりに使用するが、`dynamic_cast`演算子。 その基本クラスのいずれかに MI を持つオブジェクトをキャストすると、コンパイラに指定された基底クラスの関数が使用されます。 詳細については、次を参照してください。 [dynamic_cast Operator](../cpp/dynamic-cast-operator.md)します。

## <a name="cobject---the-root-of-all-classes"></a>CObject のすべてのクラスのルート

すべての重要なクラスがクラスから直接的または間接的に派生`CObject`します。 `CObject` メンバー データがありませんが、いくつかの既定の機能が。 多重継承を使用する場合は通常を継承する 2 つ以上の`CObject`-クラスを派生します。 次の例がクラスから継承されるしくみを示しています、 [CFrameWnd](../mfc/reference/cframewnd-class.md)と[CObList](../mfc/reference/coblist-class.md):

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

ここで`CObject`2 つの時刻が含まれています。 参照のあいまいさを解消する方法を必要とされる、この`CObject`メソッドまたは演算子。 **演算子 new**と[delete 演算子](../mfc/reference/cobject-class.md#operator_delete)2 つの演算子は、あいまいさを解決する必要があります。 別の例としては、次のコードは、コンパイル時に、エラーを発生します。

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>CObject メソッドを再実装

2 つ以上を搭載する新しいクラスを作成する場合`CObject`、基本クラスを派生する必要があります、`CObject`メソッドを使用するには、他のユーザーします。 演算子**新しい**と**削除**は必須と[ダンプ](../mfc/reference/cobject-class.md#dump)をお勧めします。 次の例 reimplements、**新しい**と**削除**演算子および`Dump`メソッド。

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>CObject の仮想継承

その仮想継承するかもしれませんが`CObject`関数のあいまいさの問題を解決するが、そうでないです。 メンバーのデータがないため`CObject`、仮想継承の基本クラスのメンバー データの複数のコピーを回避する必要はありません。 以前に示した最初の例で、`Dump`は異なる方法で実装されるため、仮想メソッドがあいまいです。`CFrameWnd`と`CObList`します。 あいまいさを排除する最善の方法では、前のセクションで提示された推奨事項に従ってください。

## <a name="cobjectiskindof-and-run-time-typing"></a>使うため、実行時の入力

MFC でサポートされる実行時入力メカニズム`CObject`DECLARE_DYNAMIC、IMPLEMENT_DYNAMIC、DECLARE_DYNCREATE、IMPLEMENT_DYNCREATE、DECLARE_SERIAL および IMPLEMENT_SERIAL マクロを使用します。 これらのマクロは、安全なダウン キャストを実行時の型チェックを実行できます。

これらのマクロは、1 つの基底クラスのみをサポートを多重継承クラスの限定された方法で動作します。 新規クラスまたは IMPLEMENT_SERIAL で指定する基本クラスは、最初 (または、左端の) 基底クラスである必要があります。 この配置では、型チェックの一番左の基底クラスのみを実行することを有効になります。 実行時の型システムを使用して、他の基本クラスはわかりません。 実行時のシステムを実行する次の例では、型に対してチェック`CFrameWnd`、について何も知ってされますが、`CObList`します。

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd とメッセージ マップ

正常に機能するには、MFC メッセージ マップ システムには、2 つの追加要件があります。

- 1 つだけあります`CWnd`-基底クラスを派生します。

- `CWnd`-派生の基本クラスは、最初 (または、左端の) の基本クラスである必要があります。

ここでは動作しないいくつかの例に示します。

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>多重継承を使用してサンプル プログラム

次のサンプルは、スタンドアロン アプリケーションの 1 つから派生クラスで構成される`CFrameWnd`と[CWinApp](../mfc/reference/cwinapp-class.md)します。 この方法でアプリケーションを構成するが、これは、1 つのクラスを含む最小の MFC アプリケーションの例はお勧めできません。

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

    // Necessary because of MI disambiguity
    void* operator new(size_t nSize)
        { return CFrameWnd::operator new(nSize); }
    void operator delete(void* p)
        { CFrameWnd::operator delete(p); }

    // Implementation
    // CWinApp overrides
    virtual BOOL InitInstance();
    // CFrameWnd overrides
    virtual void PostNcDestroy();
    afx_msg void OnPaint();

    DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

// because the frame window is not allocated on the heap, we must
// override PostNCDestroy not to delete the frame object
void CHelloAppAndFrame::PostNcDestroy()
{
    // do nothing (do not call base class)
}

void CHelloAppAndFrame::OnPaint()
{
    CPaintDC dc(this);
    CRect rect;
    GetClientRect(rect);

    CString s = "Hello, Windows!";
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));
    dc.SetBkMode(TRANSPARENT);
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);
}

// Application initialization
BOOL CHelloAppAndFrame::InitInstance()
{
    // first create the main frame
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",
        WS_OVERLAPPEDWINDOW, rectDefault))
        return FALSE;

    // the application object is also a frame window
    m_pMainWnd = this;
    ShowWindow(m_nCmdShow);
    return TRUE;
}

CHelloAppAndFrame theHelloAppAndFrame;
```

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
