---
title: FreeLibrary と AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: 0b530aca2ab036de186ff3fdb11be23f41e12d05
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821552"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary と AfxFreeLibrary

Dll に明示的にリンクしているプロセスは、DLL モジュールが不要になったときに[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)関数を呼び出します。 この関数は、モジュールの参照カウントをデクリメントします。 また、参照カウントが0の場合は、プロセスのアドレス空間からマップ解除されます。

Mfc アプリケーションでは、mfc 拡張 DLL を`FreeLibrary`アンロードするために、の代わりに [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) を使用します。 `AfxFreeLibrary` のインターフェイス (関数プロトタイプ) は `FreeLibrary`と同じです。

## <a name="what-do-you-want-to-do"></a>作業内容

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md#linking-implicitly)

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [LoadLibrary と AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>関連項目

[Visual Studio でC++の C/dll の作成](dlls-in-visual-cpp.md)\
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)\
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
