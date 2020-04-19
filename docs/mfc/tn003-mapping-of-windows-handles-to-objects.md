---
title: テクニカル ノート 3:オブジェクトへの Windows ハンドルのマッピング
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 45492963e1b686e03eb59c320fdc3d52d1534f7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513540"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>テクニカル ノート 3:オブジェクトへの Windows ハンドルのマッピング

このメモでは、オブジェクトへC++の Windows オブジェクトハンドルのマッピングをサポートする MFC ルーチンについて説明します。

## <a name="the-problem"></a>問題を

Windows オブジェクトは、通常、さまざまな[ハンドル](/windows/win32/WinProg/windows-data-types)オブジェクトによって表されます。 C++ MFC クラスは、オブジェクトを使用して windows オブジェクトハンドルをラップします。 MFC クラスライブラリのハンドルラッピング関数を使用すると、特定C++のハンドルを持つ Windows オブジェクトをラップしているオブジェクトを見つけることができます。 ただし、オブジェクトにC++ラッパーオブジェクトが含まれておらず、これらの時点で、 C++ラッパーとして機能する一時オブジェクトが作成される場合もあります。

ハンドルマップを使用する Windows オブジェクトは次のとおりです。

- HWND ([CWnd](../mfc/reference/cwnd-class.md)および`CWnd`-derived クラス)

- HDC ([CDC](../mfc/reference/cdc-class.md)および`CDC`-derived クラス)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- SOCKET ([CSocket](../mfc/reference/csocket-class.md))

これらのオブジェクトのいずれかのハンドルを指定すると、静的メソッド`FromHandle`を呼び出すことによって、ハンドルをラップする MFC オブジェクトを見つけることができます。 たとえば、hwnd が hwnd の場合、次の行は*hwnd*をラップするへの`CWnd`ポインターを返します。

```
CWnd::FromHandle(hWnd)
```

*Hwnd*に特定のラッパーオブジェクトがない場合は、 `CWnd` *hwnd*をラップするための一時的なが作成されます。 これにより、任意のハンドルからC++有効なオブジェクトを取得できます。

ラッパーオブジェクトを作成した後は、ラッパークラスのパブリックメンバー変数からハンドルを取得できます。 の`CWnd`場合、 *m_hWnd*にはそのオブジェクトの hWnd が含まれています。

## <a name="attaching-handles-to-mfc-objects"></a>アタッチ (ハンドルを MFC オブジェクトに)

新しく作成されたハンドルラッパーオブジェクトと Windows オブジェクトへのハンドルを指定した場合、この例のよう`Attach`に関数を呼び出すことによって、2つを関連付けることができます。

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

これにより、 *myWnd*と*hWnd*を関連付けるパーマネントマップにエントリが作成されます。 を`CWnd::FromHandle(hWnd)`呼び出すと、 *myWnd*へのポインターが返されるようになります。 *MyWnd*が削除されると、デストラクターは、Windows の[DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow)関数を呼び出すことによって*hWnd*を自動的に破棄します。 これが望ましくない場合は、 *myWnd*が破棄される前に、 *myWnd*から*hWnd*をデタッチする必要があります (通常、 *myWnd*が定義されているスコープを離れる場合)。 メソッド`Detach`はこれを行います。

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>一時オブジェクトの詳細

まだラッパーオブジェクトを持っ`FromHandle`ていないハンドルがに指定されている場合、一時オブジェクトが作成されます。 これらの一時オブジェクトは、ハンドルからデタッチされ、 `DeleteTempMap`関数によって削除されます。 既定では、 [CWinThread:: OnIdle](../mfc/reference/cwinthread-class.md#onidle)は、一時ハンドルマップをサポートする各クラスに対して自動的にを呼び出し`DeleteTempMap`ます。 これは、一時オブジェクトへのポインターが、ポインターが取得された関数からの終了位置を越えて有効であると想定できないことを意味します。

## <a name="wrapper-objects-and-multiple-threads"></a>ラッパーオブジェクトと複数のスレッド

一時オブジェクトとパーマネントオブジェクトは、スレッドごとに保持されます。 つまり、あるスレッドが、一時的か永続的かC++に関係なく、別のスレッドのラッパーオブジェクトにアクセスすることはできません。

これらのオブジェクトをあるスレッドから別のスレッドに渡すには、常`HANDLE`にネイティブ型として送信します。 あるスレッドC++から別のスレッドにラッパーオブジェクトを渡すと、多くの場合、予期しない結果が発生します。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
