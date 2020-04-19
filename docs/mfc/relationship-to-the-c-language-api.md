---
title: C 言語 API との関係
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 8601dd034dbd73ac035084ad57c51f62e333fd32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511855"
---
# <a name="relationship-to-the-c-language-api"></a>C 言語 API との関係

Microsoft Foundation Class (MFC) ライブラリを Windows の他のクラスライブラリとは別に設定する1つの特性は、C 言語で記述された Windows API に非常に近いマッピングです。 さらに、一般に、Windows API を直接呼び出すことで、クラスライブラリへの呼び出しを自由に混在させることができます。 ただし、この直接アクセスでは、クラスがその API の完全な置換であることを意味します。 開発者は、 [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor)や[GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)など、一部の Windows 関数に対して直接呼び出しを行う必要がある場合もあります。 Windows 関数は、そのための明確な利点がある場合にのみ、クラスメンバー関数によってラップされます。

Windows のネイティブ関数呼び出しを行うことが必要になる場合があるため、C 言語の Windows API ドキュメントにアクセスできる必要があります。 このドキュメントは、Microsoft Visual C++に含まれています。

> [!NOTE]
>  MFC ライブラリフレームワークの動作の概要については、「 [Windows 用のアプリケーションを記述するためのクラスの使用](../mfc/using-the-classes-to-write-applications-for-windows.md)」を参照してください。

## <a name="see-also"></a>関連項目

[一般的なクラス デザインの考え方](../mfc/general-class-design-philosophy.md)
