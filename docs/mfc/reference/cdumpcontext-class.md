---
title: CDumpContext クラス
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: a5b53ced4e20c920aab8e7ebcda3e3f6f8798ba5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164099"
---
# <a name="cdumpcontext-class"></a>CDumpContext クラス

人が読み取ることができる形式でテキストを出力するために、ストリームに依存した診断出力をサポートします。

## <a name="syntax"></a>構文

```
class CDumpContext
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|`CDumpContext` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|16 進形式で指定したアイテムをダンプします。|
|[CDumpContext::Flush](#flush)|ダンプ コンテキスト バッファー内のデータをフラッシュします。|
|[CDumpContext::GetDepth](#getdepth)|ダンプの深さに対応する整数値を取得します。|
|[CDumpContext::HexDump](#hexdump)|16 進数形式で、配列内に含まれるバイトをダンプします。|
|[CDumpContext::SetDepth](#setdepth)|ダンプの深さを設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CDumpContext::operator &lt;&lt;](#operator_lt_lt)|ダンプ コンテキストには、変数およびオブジェクトを挿入します。|

## <a name="remarks"></a>Remarks

`CDumpContext` 基本クラスはありません。

使用することができます[afxDump](diagnostic-services.md#afxdump)を事前に宣言された`CDumpContext`ダンプのほとんどのオブジェクト。 `afxDump`オブジェクトは、Microsoft Foundation Class ライブラリのデバッグ バージョンでのみ使用できます。

メモリのいくつか[診断サービス](../../mfc/reference/diagnostic-services.md)使用`afxDump`出力にします。

定義済みの出力である Windows 環境`afxDump`オブジェクト、概念的に似ています、 `cerr` stream, Windows 関数を使用して、デバッガーにルーティングされます`OutputDebugString`します。

`CDumpContext`クラスには、オーバー ロードされた挿入 ( **<<**) 演算子を`CObject`オブジェクトのデータをダンプするポインター。 カスタムのダンプ形式の派生オブジェクトが必要な場合は、オーバーライド[CObject::Dump](../../mfc/reference/cobject-class.md#dump)します。 ほとんどの Microsoft Foundation classes のオーバーライドされた実装`Dump`メンバー関数。

クラスから派生していない`CObject`など`CString`、 `CTime`、および`CTimeSpan`、独自のオーバー ロードがある`CDumpContext`などの操作が頻繁に使用される構造体として、挿入演算子`CFileStatus`、`CPoint`と`CRect`.

使用する場合、 [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)または[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)マクロ、クラスの実装で`CObject::Dump`の名前を表示、 `CObject`-クラスを派生します。 それ以外の場合は印刷`CObject`します。

`CDumpContext`クラスは、ライブラリのデバッグとリリースの両方のバージョンで使用できますが、`Dump`メンバー関数は、デバッグ バージョンでのみ定義します。 使用 **#ifdef _DEBUG**  /  `#endif`ステートメントなど、カスタム、診断コードを角かっこを`Dump`メンバー関数。

独自に作成する前に`CDumpContext`オブジェクトを作成する必要があります、`CFile`ダンプ先として機能するオブジェクト。

詳細については`CDumpContext`を参照してください[MFC アプリケーションのデバッグ](/visualstudio/debugger/mfc-debugging-techniques)します。

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>継承階層

`CDumpContext`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="cdumpcontext"></a>  CDumpContext::CDumpContext

クラスのオブジェクトを構築`CDumpContext`します。

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>パラメーター

*pFile*<br/>
ポインター、`CFile`ダンプ先であるオブジェクト。

### <a name="remarks"></a>Remarks

`afxDump`オブジェクトが自動的に構築されます。

基になるにも書き込まれない`CFile`ダンプと干渉するダンプ コンテキストは、active 以外の場合は、します。 Windows 環境では、出力が Windows 関数を使用して、デバッガーにルーティングされる`OutputDebugString`します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

##  <a name="dumpashex"></a>  CDumpContext::DumpAsHex

指定した型の 16 進数値として書式設定をダンプします。

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>戻り値

`CDumpContext` オブジェクトへの参照。

### <a name="remarks"></a>Remarks

16 進数として指定した型の項目をダンプする場合は、このメンバー関数を呼び出します。 配列をダンプする[に](#hexdump)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

##  <a name="flush"></a>  CDumpContext::Flush

強制的に、ファイルに書き込まれるバッファーの残りの部分は、ダンプ コンテキストにアタッチします。

```
void Flush();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

##  <a name="getdepth"></a>  CDumpContext::GetDepth

Deep または shallow ダンプが進行中であるかどうかを判断します。

```
int GetDepth() const;
```

### <a name="return-value"></a>戻り値

によって設定されたダンプの深さ`SetDepth`します。

### <a name="example"></a>例

  例をご覧ください[SetDepth](#setdepth)します。

##  <a name="hexdump"></a>  CDumpContext::HexDump

16 進数として書式設定されたバイトの配列をダンプします。

```
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>パラメーター

*lpszLine*<br/>
新しい行の先頭に出力する文字列。

*pby*<br/>
ダンプするバイトを格納するバッファーへのポインター。

*nBytes*<br/>
ダンプするバイト数。

*nWidth*<br/>
バイトの最大数は、1 行 (出力行の幅は) にダンプします。

### <a name="remarks"></a>Remarks

16 進数として、特定の 1 つの項目の種類をダンプするには、呼び出す[CDumpContext::DumpAsHex](#dumpashex)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

##  <a name="operator_lt_lt"></a>  CDumpContext::operator &lt;&lt;

ダンプ コンテキストに指定されたデータを出力します。

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>戻り値

A`CDumpContext`参照。 戻り値を使用して、ソース コードの 1 行に複数の挿入を記述できます。

### <a name="remarks"></a>Remarks

に対して、挿入演算子がオーバー ロード`CObject`ほとんどのプリミティブ型の場合と同様のポインター。 文字列の内容のダンプに文字結果へのポインターポインター **void**のみアドレスの 16 進ダンプになります。 64 ビット符号付き整数のダンプの結果、LONGLONG64 ビット符号なし整数のダンプを ULONGLONG になります。

を通じて、クラス、挿入演算子の実装では、新規クラスまたは IMPLEMENT_SERIAL マクロを使用する場合`CObject::Dump`の名前を表示、 `CObject`-クラスを派生します。 それ以外の場合は印刷`CObject`します。 オーバーライドする場合、`Dump`クラスの関数は、16 進ダンプの代わりに、オブジェクトの内容のわかりやすい出力を提供できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

##  <a name="setdepth"></a>  CDumpContext::SetDepth

ダンプの深さを設定します。

```
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>パラメーター

*nNewDepth*<br/>
新しい深さの値。

### <a name="remarks"></a>Remarks

プリミティブ型または単純なをダンプする場合`CObject`、他のオブジェクトへのポインターが含まれていないし、0 の値で十分です。 0 = すべてのオブジェクトが深いダンプよりも大きい値では、再帰的にダンプします。 たとえば、コレクションのすべての要素をコレクションの深いダンプがダンプされます。 派生クラスで他の特定の深さの値を使用することがあります。

> [!NOTE]
>  循環参照を使用して、深いダンプでは検出されず、無限ループになることができます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFile クラス](../../mfc/reference/cfile-class.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)
