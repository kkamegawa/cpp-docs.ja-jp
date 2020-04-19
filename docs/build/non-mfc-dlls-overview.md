---
title: 非 MFC DLL:概要
ms.date: 11/04/2016
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
ms.openlocfilehash: 88afb41205e63a837d7bc134133c3c36eccf5dc1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493172"
---
# <a name="non-mfc-dlls-overview"></a>非 MFC DLL:概要

Mfc 以外の DLL は、MFC を内部で使用しない dll であり、DLL 内のエクスポートされた関数は MFC または非 MFC の実行可能ファイルによって呼び出すことができます。 通常、関数は、標準の C インターフェイスを使用して、MFC 以外の DLL からエクスポートされます。

非 MFC Dll の詳細については、「Windows SDK の[ダイナミックリンクライブラリ](/windows/win32/dlls/dynamic-link-libraries)」を参照してください。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [チュートリアル: ダイナミックリンクライブラリの作成と使用](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)

- [DLL からのエクスポート](exporting-from-a-dll.md)

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md)

- [DLL の初期化](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [MFC に静的にリンクされるレギュラー MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [MFC に動的にリンクされるレギュラー MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 拡張 DLL:概要](extension-dlls-overview.md)

## <a name="see-also"></a>関連項目

[DLL の種類](kinds-of-dlls.md)
