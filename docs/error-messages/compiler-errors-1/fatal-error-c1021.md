---
title: 致命的なエラー C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 861e768563cf737d6925d5753d80cd9269eff4fe
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756891"
---
# <a name="fatal-error-c1021"></a>致命的なエラー C1021

プリプロセッサ コマンド 'string' が無効です

`string` は無効な [プリプロセッサ ディレクティブ](../../preprocessor/preprocessor-directives.md)です。 エラーを解決するには、 `string`に有効なプリプロセッサ名を使用します。

次の例では C1021 が生成されます。

```cpp
// C1021.cpp
#BadPreProcName    // C1021 delete line
```
