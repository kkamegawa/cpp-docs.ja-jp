---
title: Windows Sockets クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 4abdd8f8fbfc115b5014ffd0b3a37df357852b16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371803"
---
# <a name="windows-sockets-classes"></a>Windows Sockets クラス

Windows ソケットは、2 台のコンピューター間で通信するネットワーク プロトコルに依存しない方法を提供します。 これらのソケットを同期することができます (プログラムは、通信が完了するまで待機する) または非同期 (プログラムの継続での通信が行われている)。

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
シン ラッパーで Windows ソケット API をカプセル化します。

[CSocket](../mfc/reference/csocket-class.md)<br/>
高いレベルの抽象化から派生した`CAsyncSocket`します。 同期的に動作します。

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
提供、 `CFile` Windows ソケット インターフェイス。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
