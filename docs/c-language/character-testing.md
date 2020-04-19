---
title: 文字テスト
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740096"
---
# <a name="character-testing"></a>文字テスト

**ANSI 4.3.1** `isalnum`、`isalpha`、`iscntrl`、`islower`、`isprint`、`isupper` 関数がテストする文字セット

次の一覧は、Microsoft C コンパイラによって実装された、これらの関数について説明します。

|関数|テスト対象|
|--------------|---------------|
|`isalnum`|文字 0 - 9、A - Z、a - z、ASCII 48 - 57、65 - 90、97 - 122|
|`isalpha`|文字 A - Z、a - z、ASCII 65 - 90、97 - 122|
|`iscntrl`|ASCII 0 - 31、127|
|`islower`|文字 a - z、ASCII 97 - 122|
|`isprint`|文字 A - Z、a - z、0 - 9、句読点、スペース、ASCII 32 - 126|
|`isupper`|文字 A - Z、ASCII 65 - 90|

## <a name="see-also"></a>関連項目

[ライブラリ関数](../c-language/library-functions.md)
