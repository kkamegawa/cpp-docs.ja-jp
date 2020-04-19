---
title: 文字セットにおける移植性の利点
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 0ca7e46cabb2d98a64a244863f8574a3e9e2a456
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410780"
---
# <a name="benefits-of-character-set-portability"></a>文字セットにおける移植性の利点

現在しないアプリケーションを国際化する場合でも、MFC および C ランタイムの移植性の機能を使用して得ることができます。

- 柔軟な基本コードは、移植可能な方法でコーディングします。 後で移動できます簡単に Unicode や MBCS にします。

- 効率的な Windows のアプリケーションは、Unicode を使用します。 Windows では、Unicode を使用するため、オペレーティング システムとの間に渡される Unicode 以外の文字列変換される必要が、オーバーヘッドが発生します。

## <a name="see-also"></a>関連項目

[Unicode と MBCS](../text/unicode-and-mbcs.md)<br/>
[Unicode のサポート](../text/support-for-unicode.md)
