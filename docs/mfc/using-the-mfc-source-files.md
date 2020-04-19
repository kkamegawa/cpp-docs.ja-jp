---
title: MFC ソース ファイルの利用
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ca5799da7a6ada42db20e3551b3fb7262e8990a0
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631667"
---
# <a name="using-the-mfc-source-files"></a>MFC ソース ファイルの利用

MFC (Microsoft Foundation Class) ライブラリには、完全なソースコードが用意されています。 ヘッダーファイル (.h) は、 *\ atlmfc/include*ディレクトリにあります。 実装ファイル (.cpp) は、 *\ atlmfcディレクトリ*にあります。

この記事では、MFC が各クラスのさまざまな部分をコメント化する際に使用する規則、これらのコメントの意味、および各セクションで検索する必要がある内容について説明します。 Visual Studio のウィザードでは、自分で作成したクラスに対して同様の規則が使用されるため、独自のコードにはこれらの規則が役立つ場合があります。

**Public**、 **protected**、および**private** C++キーワードについて理解している場合もあります。 MFC ヘッダーファイルでは、各クラスに複数のクラスが含まれていることがわかります。 たとえば、パブリックメンバーの変数と関数は、複数の**public**キーワードの下にある場合があります。 これは、MFC では、メンバー変数と関数が、許可されるアクセスの種類ではなく、使用方法に基づいて分離されるためです。 MFC では、控えめに使用します。 実装の詳細と見なされる項目も**保護**され、多くの場合、**パブリック**になります。 実装の詳細へのアクセスは推奨されていませんが、MFC では決定を行いません。

Mfc のソースファイルと MFC アプリケーションウィザードによって作成されるヘッダーファイルの両方で、次のようなコメントがクラス宣言 (通常はこの順序) に含まれています。

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a>コメントの例

クラス`CStdioFile`の次の部分的な一覧では、MFC でクラスによって使用される標準的なコメントのほとんどを使用して、クラスのメンバーを使用方法によって分割しています。

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

これらのコメントは、類似した種類のクラスメンバーを含むクラス宣言のセクションを常にマークします。 これらは MFC の規則であり、規則が設定されていないことに注意してください。

## <a name="-constructors-comment"></a>コンストラクターコメント

MFC `// Constructors`クラス宣言のセクションでは、コンストラクター ( C++意味) と、オブジェクトを実際に使用するために必要な初期化関数を宣言します。 たとえば、 `CWnd::Create`は、 `CWnd`オブジェクトを使用する前に、 C++コンストラクターを呼び出してから`Create`関数を呼び出すことによって "完全に構築" される必要があるため、コンストラクターセクション内にあります。 通常、これらのメンバーはパブリックです。

たとえば、クラス`CStdioFile`には5つのコンストラクターがあり、そのうちの1つが[コメントの例](#an-example-of-the-comments)の下に一覧表示されます。

## <a name="-attributes-comment"></a>属性のコメント

MFC `// Attributes`クラス宣言のセクションには、オブジェクトのパブリック属性 (またはプロパティ) が含まれています。 通常、属性はメンバー変数、または Get/Set 関数です。 "Get" 関数と "Set" 関数は、仮想にすることも、使用することもできません。 多くの場合、"Get" 関数は**定数**になります。これは、ほとんどの場合、副作用がないためです。 通常、これらのメンバーはパブリックです。 Protected 属性と private 属性は、通常、実装セクションにあります。

クラス`CStdioFile`のサンプルリストでは、[コメントの例](#an-example-of-the-comments)として、リストに1つのメンバー変数*m_pStream*が含まれています。 クラス`CDC`は、このコメントの下に約20個のメンバーを一覧表示します。

> [!NOTE]
> `CDC` や`CWnd`などの大規模なクラスでは、1つのグループ内のすべての属性を一覧表示するだけでは、わかりにくくなることはありません。 このような場合、クラスライブラリは、他のコメントを見出しとして使用し、メンバーをさらに詳細に記述します。 たとえば、 `CDC`は、、 `// Drawing Tool Functions`、 `// Drawing Attribute Functions`などを使用`// Device-Context Functions`します。 属性を表すグループは、上で説明した通常の構文に従います。 多くの OLE クラスには、と`// Interface Maps`いう実装セクションがあります。

## <a name="-operations-comment"></a>操作のコメント

MFC クラスの宣言のセクションには、オブジェクトに対して呼び出すことができるメンバー関数が含まれています。これにより、オブジェクトを処理したり、アクションを実行したり(操作を実行)することができます。`// Operations` これらの関数は、通常、副作用があるため、通常は非**定数**です。 これらは、クラスのニーズに応じて、仮想でも非仮想でもかまいません。 通常、これらのメンバーはパブリックです。

クラス`CStdioFile`からのサンプルリストでは、[コメントの例](#an-example-of-the-comments) `WriteString`として、このコメントの下に3つのメンバー関数が含まれ`ReadString`ています。また、の2つのオーバーロードがあります。

属性と同様に、操作はさらに細かく分割できます。

## <a name="-overridables-comment"></a>Overridables コメント

MFC `// Overridables`クラスの宣言のセクションには、基底クラスの動作を変更する必要がある場合に派生クラスでオーバーライドできる仮想関数が含まれています。 これらの名前は、通常、"On" で始まりますが、厳密には必要ありません。 ここで示した関数はオーバーライドされるように設計されており、多くの場合、何らかの種類の "コールバック" または "フック" を実装または提供します。 通常、これらのメンバーは保護されています。

MFC 自体では、純粋仮想関数は常にこのセクションに配置されます。 のC++純粋仮想関数は、次の形式をとります。

`virtual void OnDraw( ) = 0;`

クラス`CStdioFile`のサンプルリストでは、[コメントの例](#an-example-of-the-comments)として、リストに overridables セクションが含まれていません。 一方`CDocument`、クラスには、約10個のオーバーライド可能なメンバー関数が一覧表示されます。

一部のクラスでは、コメント`// Advanced Overridables`も表示される場合があります。 これらの関数は、高度なプログラマだけがオーバーライドを試みる必要があります。 オーバーライドする必要はありません。

> [!NOTE]
> この記事で説明されている規則は、一般に、オートメーション (旧称 OLE オートメーション) のメソッドとプロパティに対しても正常に機能します。 オートメーションメソッドは、MFC 操作に似ています。 オートメーションプロパティは、MFC 属性に似ています。 オートメーションイベント (ActiveX コントロールでサポートされていた従来の OLE コントロール) は、MFC でオーバーライドできるメンバー関数に似ています。

## <a name="-implementation-comment"></a>実装コメント

この`// Implementation`セクションは、MFC クラスの宣言の中で最も重要な部分です。

ここでは、すべての実装の詳細について説明します。 このセクションには、メンバー変数とメンバー関数の両方を含めることができます。 この行の下にあるすべてのものは、MFC の今後のリリースで変更される可能性があります。 それを回避できない限り、行の`// Implementation`下の詳細には依存しないでください。 また、実装行の下で宣言されたメンバーについては文書化されていませんが、一部の実装については、テクニカルノートを参照してください。 基本クラスの仮想関数のオーバーライドは、で基本クラス関数が定義されているセクションに関係なく、このセクションに存在します。 関数が基底クラスの実装をオーバーライドする場合は、実装の詳細と見なされます。 通常、これらのメンバーは保護されていますが、常にではありません。

[コメントの例の](#an-example-of-the-comments)下の`// Implementation`一覧では、コメントの下で宣言されたメンバーは、public、protected、または private として宣言されている可能性が`CStdioFile`あります。 これらのメンバーは将来変更される可能性があるため、注意して使用してください。 クラスライブラリの実装が正しく機能するためには、メンバーのグループを**パブリック**として宣言する必要がある場合があります。 ただし、宣言されたようにメンバーを安全に使用できるとは限りません。

> [!NOTE]
> 残りの種類のコメントは、コメントの`// Implementation`上または下に表示される場合があります。 どちらの場合も、その下で宣言されたメンバーの種類を記述します。 コメントの`// Implementation`下に出現する場合は、メンバーが MFC の将来のバージョンで変更される可能性があることを前提としています。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
