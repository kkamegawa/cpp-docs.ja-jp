---
title: 変換:診断
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152600"
---
# <a name="translation-diagnostics"></a>変換:診断

**ANSI 2.1.1.3** 診断を識別する方法

Microsoft C は、次の形式のエラー メッセージを生成します。

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

ここで、*filename* はエラーが発生したソース ファイルの名前、*line-number* はコンパイラがエラーを検出した行番号、*diagnostic* は "error" または "warning"、*number* は (構文に示すように先頭に **C** が付いた) 一意の 4 桁の番号、*message* は説明メッセージです。

## <a name="see-also"></a>関連項目

[実装で定義された動作](../c-language/implementation-defined-behavior.md)
