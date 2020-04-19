---
title: ML の致命的なエラー A1017
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 523fed26afae5a88c5f154283487d3453a2e48c7
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318060"
---
# <a name="ml-fatal-error-a1017"></a>ML の致命的なエラー A1017

**ソースファイル名がありません**

ML が、リンカーにアセンブルまたは渡すファイルを見つけることができませんでした。

このエラーは、操作するファイル名を指定せずに ML コマンドラインオプションを指定した場合に生成されます。 拡張子が .asm ではないファイルをアセンブルするには、 **/Ta**コマンドラインオプションを使用します。

ML 環境変数にコマンドラインオプションが含まれている場合は、パラメーターを指定せずに ML を呼び出すことで、このエラーを生成することもできます。

## <a name="see-also"></a>関連項目

[ML エラー メッセージ](ml-error-messages.md)
