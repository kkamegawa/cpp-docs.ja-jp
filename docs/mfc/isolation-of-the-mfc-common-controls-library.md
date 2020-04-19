---
title: MFC コモン コントロール ライブラリの分離
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
ms.openlocfilehash: 94700f850be62404f22974a1d5e76acad711555c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310865"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>MFC コモン コントロール ライブラリの分離

コモン コントロール ライブラリは (ユーザーの Dll) などのさまざまなモジュールを許可する MFC 内で分離ようになりましたが、マニフェストのバージョンを指定することで別のバージョンのコモン コントロール ライブラリを使用します。

MFC アプリケーション (または MFC で呼び出されたユーザー コード) は、ラッパー関数を使用して Api という名前のコモン コントロール ライブラリの呼び出しを`Afx` *FunctionName*ここで、 *FunctionName*共通の名前を指定しますAPI を制御します。 Afxcomctl32.h と afxcomctl32.inl はでは、そのラッパー関数が定義されています。

使用することができます、 [AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists)と[AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2)コモン コントロール ライブラリで呼び出す代わりに特定の API を実装するかどうかを確認するマクロ (afxcomctl32.h に定義されている)[GetProcAddress](../build/getprocaddress.md)します。

技術的には、ラッパー クラスでは、一般的なコントロール ライブラリの Api への呼び出しを行った`CComCtlWrapper`(afxcomctl32.h に定義されています)。 `CComCtlWrapper` ロードとアンロードの comctl32.dll の責任を負います。 MFC モジュール状態のインスタンスへのポインターを格納する`CComCtlWrapper`します。 ラッパー クラスを使用して、アクセスすることができます、`afxComCtlWrapper`マクロ。

呼び出して共通コントロール API を直接 (MFC のラッパー関数を使用していない)、MFC からアプリケーションまたはユーザーの DLL はほとんどの場合、MFC アプリケーションまたは DLL をユーザーが要求したマニフェストでコモン コントロール ライブラリにバインドされているため)。 ただし、MFC コードは、さまざまなコモン コントロール ライブラリのバージョンでのユーザーの Dll から呼び出される可能性があるために、MFC コード自体は、ラッパーを使用するがします。
