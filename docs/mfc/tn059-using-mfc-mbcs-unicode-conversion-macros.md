---
title: TN059:MFC の MBCS、Unicode 変換マクロの使用
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: 6c182ff584404fb91de8ff5e8020ec2e6ef9f950
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611859"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059:MFC の MBCS または Unicode 変換マクロの使用

> [!NOTE]
>  次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

ここでは、MBCS または Unicode 変換で AFXPRIV で定義されているマクロを使用する方法について説明します。H. これらのマクロは、アプリケーション取引直接 OLE API を使用した、または何らかの理由は、多くの場合、必要な Unicode と MBCS 変換する場合に特に役立ちます。

## <a name="overview"></a>概要

Mfc 3.x、特別な DLL が (MFCANS32 の使用します。DLL) をクリックし、OLE インターフェイスが呼び出されたときに、Unicode と MBCS の間で自動的に変換します。 この DLL が常に Unicode があるにもかかわらず、OLE Api とインターフェイスが MBCS、まるで書き込まれる OLE アプリケーションが許可されているレイヤーを透明に近い (Macintosh 上を除く)。 このレイヤーは便利でしたができ、アプリケーションの Win16 から Win32 にすばやく移植 (MFC、Microsoft Word、Excel、および VBA ではこのテクノロジを使用する Microsoft アプリケーションの一部)、大幅なパフォーマンスがヒットします。 このため、MFC 4.x この DLL は使用されないため、代わりに Unicode OLE インターフェイスに直接通信します。 これを行うには、MFC は、OLE インターフェイスへの呼び出しを行うときに、MBCS、Unicode に変換する必要があり、多くの場合、OLE インターフェイスを実装する場合は、Unicode から MBCS に変換する必要があります。 簡単かつ効率的には、これを処理するために、いくつかのマクロは、この変換を容易に作成されました。

マクロのセットを作成する最も大きな難関の 1 つは、メモリの割り当てです。 文字列をインプレース変換できないため、変換した結果を格納する新しいメモリを割り当てる必要があります。 これでしたが完了すると、次のようなコード。

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

この方法には、さまざまな問題では。 主な問題は、大量の記述、テスト、およびデバッグするコードです。 単純な関数呼び出しが、はるかに複雑になっているものです。 さらに、これにオーバーヘッドが大幅なランタイムがあります。 メモリがヒープに割り当てられ、変換が行われるたびに解放される必要があります。 最後に、上記のコードが必要に適切な`#ifdefs`(これを行うには、この変換を必要としない)、Unicode と Mac のビルドに追加します。

そうと、ソリューションでは、ソース コードをどのマスク 1) さまざまなプラットフォーム、および 2) を使用した、効率的なメモリの割り当て方法の違いと 3) は、既存に挿入する簡単ないくつかのマクロを作成します。 定義を 1 つの例を次に示します。

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

この上記のコードではなくマクロと処理を使用することはとても簡単です。

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

変換が必要に応じてが簡単で効果的なは、マクロを使用して、余分な呼び出しがあります。

各マクロの実装では、ヒープではなく、スタックからメモリを割り当てる場合、_alloca() 関数を使用します。 ヒープ上のメモリを割り当てる場合よりもはるかに高速では、スタックからメモリを割り当てると、メモリは、関数が終了したときに自動的に解放します。 さらに、呼び出すことは避け、マクロ`MultiByteToWideChar`(または`WideCharToMultiByte`) 1 つ以上の時間。 これは、必要なはよりもう少し多くのメモリを割り当てることによって行います。 MBC は多くて 1 つに変換されていることがわかって**WCHAR**と各**WCHAR** 2 文字の最大必要があります。 必ずが少々 必要に応じて、割り当てることによって、変換、2 番目の呼び出しを次に処理するために、変換関数への呼び出しを回避できます。 ヘルパー関数を呼び出す`AfxA2Whelper`変換を実行するために行う必要がある引数のプッシュの数を減らします (この結果より小さなコードよりも呼び出される場合`MultiByteToWideChar`直接)。

格納する領域がないマクロの順序で、変換マクロを使用するは、各関数を変換 (_c) と呼ばれるローカル変数を宣言する必要がある一時の長さ。 これは、上記の例に示すように、USES_CONVERSION マクロを呼び出すことによって行います。

汎用変換マクロと OLE 固有のマクロの両方があります。 これら 2 つの異なるマクロのセットを以下に示します。 すべてのマクロは AFXPRIV 内に存在します。H.

## <a name="generic-conversion-macros"></a>汎用変換マクロ

汎用変換マクロは、基になるメカニズムを形成します。 マクロの例と A2W、前のセクションで示す実装は、このような 1 つの「汎用」マクロです。 OLE に具体的には関連してがありません。 ジェネリックのマクロのセットは、次に示します。

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

テキスト変換を行うだけでなくもマクロおよび変換するためのヘルパー関数`TEXTMETRIC`、 `DEVMODE`、 `BSTR`、および OLE 文字列が割り当てられています。 これらのマクロは、この説明の範囲を超えています - AFXPRIV を参照してください。これらのマクロの詳細については H します。

## <a name="ole-conversion-macros"></a>OLE 変換マクロ

OLE 変換マクロが予想される関数の処理用に設計された**OLESTR**文字。 OLE ヘッダーを確認する場合に多くの参照が表示されます**LPCOLESTR**と**OLECHAR**します。 これらの型は、プラットフォームに固有でない方法での OLE インターフェイスで使用される文字の型を参照に使用されます。 **OLECHAR**マップ**char** Win16 と Macintosh プラットフォームと**WCHAR** Win32 でします。

数を維持するために **#ifdef**ディレクティブ、MFC でのコードを最小限に変換ごとのようなマクロがあることを OLE 文字列が含まれる場所。 次のマクロがよく使用されます。

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

ここでも、受け取る、DEVMODE、BSTR、および OLE 文字列の割り当てを行うための類似のマクロがあります。 AFXPRIV を参照してください。詳細については H します。

## <a name="other-considerations"></a>その他の注意事項

ループの中で、マクロを使わないでください。 たとえば、次のようなコードを記述することはおたくないです。

```
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

上記のコードは、どのような文字列の内容によってスタックにメモリのメガバイト数の割り当てになる可能性があります`lpsz`です! また、ループの反復ごとに文字列に変換する時間がかかります。 代わりに、ループの外にこのような定数の変換を移動します。

```
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

文字列が定数でない場合は、関数のメソッド呼び出しをカプセル化します。 これは、毎回解放する変換バッファーで許可されます。 例:

```
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

戻り値は、戻り値の前に、データのコピーを作成することを意味しない限り、マクロのいずれかの結果を返すことはありません。 たとえば、このコードが正しくありません。

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

上記のコードは、値がコピーされるように、戻り値を変更することによって修正でした。

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

マクロは使いやすいと、コードに簡単に挿入しますが、上記の注意事項から分かるように、これらを使用するときに注意する必要があります。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
