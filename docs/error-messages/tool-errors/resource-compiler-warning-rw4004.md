---
title: リソース コンパイラの警告 RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: bafd1084a665fc656fe184064a48e5fffc61c957
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346081"
---
# <a name="resource-compiler-warning-rw4004"></a>リソース コンパイラの警告 RW4004

仮想キー コードに相当しない ASCII 文字

VIRTKEY 型アクセラレータの仮想キー コードに文字列リテラルが使用されました。

この警告では、処理を続行できますが、生成されたアクセラレータ キーが指定した文字列と一致しない可能性があることに注意してください。 (VIRTKEY は、ASCII アクセラレータとは異なるキー コードを使用します。)

使用して、アクセラレータを入手することを確認する文字列リテラルは構文的に有効ですが、のみできます、 **vk _\* #define** WINDOWS.h の値。