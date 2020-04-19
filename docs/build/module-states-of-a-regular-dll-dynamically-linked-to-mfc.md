---
title: MFC と動的にリンクされているレギュラー MFC DLL のモジュール状態
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220583"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>MFC と動的にリンクされているレギュラー MFC DLL のモジュール状態

レギュラー MFC DLL が MFC DLL に動的にリンクする機能は、非常に複雑になっているいくつかの構成を使用します。 たとえば、レギュラー MFC DLL とそれを使用する実行可能ファイル両方動的にリンクできます MFC DLL にし、任意の MFC 拡張 Dll にします。

この構成には問題に関して現在へのポインターなど、MFC のグローバル データ`CWinApp`オブジェクトおよびハンドル マップします。

MFC バージョン 4.0 前に、は、このグローバルなデータは、MFC DLL 内にありし、プロセス内のすべてのモジュールによって共有されました。 Win32 DLL を使用する各プロセスが独自の DLL のデータのコピーを取得するため、このスキームには、プロセスごとのデータを追跡する簡単な方法が用意されています。 また、AFXDLL モデルがあると 1 つだけと見なされますので`CWinApp`オブジェクトと 1 つだけの一連の処理のプロセス内の対応付け、MFC DLL 自体でこれらの項目を追跡する可能性があります。

レギュラー MFC DLL を MFC DLL に動的にリンクすることができます、ここで 2 つ以上を含めることは可能`CWinApp`プロセス内のオブジェクト、およびハンドルのマップの 2 つ以上のセットもします。 方法は MFC の追跡が使用するものですか。

ソリューションでは、このグローバル状態情報のコピー (アプリケーションまたはレギュラー MFC DLL) は、各モジュールを提供します。 呼び出しではそのため、 **AfxGetApp** MFC DLL は、定期的なへのポインターを返します、 `CWinApp` 実行可能ファイル、DLL 内のオブジェクト。 MFC のグローバル データの場合は、このモジュールのコピーはモジュールの状態と呼ばれます、、「 [MFC テクニカル ノート 58](../mfc/tn058-mfc-module-state-implementation.md)します。

レギュラー MFC DLL に実装されているすべてのメッセージ ハンドラーで気にする必要はありませんので、MFC の一般的なウィンドウ プロシージャは自動的に適切なモジュールの状態に切り替わります。 ただし、レギュラー MFC DLL を呼び出すと、実行可能ファイル、ときに、DLL のモジュールの現在の状態を明示的に設定する必要があります。 これを行うには、使用、 **AFX_MANAGE_STATE**マクロでは、すべての関数は DLL からエクスポートします。 これは、DLL からエクスポートされた関数の先頭に次のコード行を追加することで行います。

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [MFC モジュールの状態データを管理します。](../mfc/managing-the-state-data-of-mfc-modules.md)

- [MFC と動的にリンクされるレギュラー MFC の Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 拡張 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>関連項目

[Visual Studio で C/C++ Dll を作成します。](dlls-in-visual-cpp.md)
