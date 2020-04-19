---
title: プログラムによる印刷
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
ms.openlocfilehash: eb8804610832f91f4b24487fddfe9c24a3799117
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342091"
---
# <a name="programmatic-printing"></a>プログラムによる印刷

OLE には、永続的なドキュメントを一意に識別するための手段が提供されている (`GetClassFile`) と、関連付けられているコードに読み込むには (`CoCreateInstance`、 `QueryInterface(IID_IPersistFile)`、 `QueryInterface(IID_IPersistStorage)`、 `IPersistFile::Load`、および`IPersistStorage::Load`)。 Active ドキュメント コンテインメントの (OLE 2.0 に付属していない既存の OLE デザインを使用して) ドキュメントの印刷をさらに有効にするにはベースの標準印刷インターフェイスが導入されています`IPrint`読み込むことができる任意のオブジェクトで利用可能、ドキュメントの種類の永続的な状態です。 アクティブなドキュメントの各ビューをサポートできます必要に応じて、`IPrint`これらの機能を提供するインターフェイス。

`IPrint`インターフェイスは次のように定義されます。

```
interface IPrint : IUnknown
    {
    HRESULT SetInitialPageNum([in] LONG nFirstPage);
    HRESULT GetPageInfo(
        [out] LONG *pnFirstPage,
        [out] LONG *pcPages);
    HRESULT Print(
        [in] DWORD grfFlags,
        [in,out] DVTARGETDEVICE **pptd,
        [in,out] PAGESET ** ppPageSet,
        [in,out] STGMEDIUM **ppstgmOptions,
        [in] IContinueCallback* pCallback,
        [in] LONG nFirstPage,
        [out] LONG *pcPagesPrinted,
        [out] LONG *pnPageLast);
    };
```

クライアントとコンテナーを使用`IPrint::Print`にそのドキュメントが読み込まれる、印刷コントロール フラグ、ターゲット デバイス、印刷するページを指定すると、それ自体を印刷するドキュメントを指示して、追加オプション。 クライアントは、インターフェイスを介して印刷の継続も制御できます`IContinueCallback`(下記参照)。

さらに、`IPrint::SetInitialPageNum`番号によって 1 つのページにシームレスに明らかに Office バインダーなどの active ドキュメント コンテナー向けの特典として、一連のドキュメントを印刷する機能をサポートします。 `IPrint::GetPageInfo` により開始を取得する呼び出し元を許可することで単純なページ割り当て情報を表示するページ番号が以前に渡される`SetInitialPageNum`(またはドキュメントの内部の既定の開始ページ番号) と、ドキュメント内のページ数。

オブジェクトをサポートする`IPrint`オブジェクトの CLSID で格納されている"Printable"キーで、レジストリでマークされます。

HKEY_CLASSES_ROOT\CLSID\\{...}\Printable

`IPrint` 同じオブジェクトをサポートしていますが、通常は実装されている`IPersistFile`または`IPersistStorage`します。 呼び出し元には、"Printable"キーのレジストリでクラスのいくつかの永続的な状態をプログラムにより印刷する機能に注意してください。 現時点では、「印刷可能な」のサポートを指定には少なくとも`IPrint`; 他のインターフェイスが定義されて、今後利用し、なります`QueryInterface`場所`IPrint`単にベース レベルのサポートを表します。

印刷処理中には、クライアントまたは印刷の継続するかどうかを制御する印刷を開始したコンテナーをする可能性があります。 たとえば、コンテナーをできるだけ早く、印刷ジョブを終了する"停止 Print"コマンドをサポートできます。 印刷可能なオブジェクトのクライアントが、インターフェイスを使用して、小規模の通知シンク オブジェクトの実装時にこの機能をサポートする`IContinueCallback`:

```
interface IContinueCallback : IUnknown
    {
    HRESULT FContinue(void);
    HRESULT FContinuePrinting(
        [in] LONG cPagesPrinted,
        [in] LONG nCurrentPage,
        [in] LPOLESTR pszPrintStatus);
    };
```

このインターフェイスは、Win32 API のさまざまな継続プロシージャの代わりとなる汎用継続コールバック関数として役立つ設計されています (など、`AbortProc`印刷用と`EnumMetafileProc`メタファイル列挙体の)。 そのためこのインターフェイスのデザインは、さまざまな時間のかかるプロセスに役立ちます。

ほとんどのジェネリックの場合、`IContinueCallback::FContinue`関数が時間のかかるプロセスのプロセスで定期的に呼び出されます。 シンク オブジェクトは、S_OK を操作を続行して、プロシージャをできるだけ早く停止する S_FALSE を返します。

`FContinue`、、、のコンテキストでは使用されません`IPrint::Print`ではなく、使用して印刷`IContinueCallback::FContinuePrint`します。 任意の印刷オブジェクトを定期的に呼び出す必要があります`FContinuePrinting`印刷ページの数、印刷されるページの数と、クライアント ("ページなどのユーザーに表示することもできますが、印刷ステータスを記述するその他の文字列を渡す5 の 19 インチ)。

## <a name="see-also"></a>関連項目

[Active ドキュメント コンテナー](../mfc/active-document-containers.md)
