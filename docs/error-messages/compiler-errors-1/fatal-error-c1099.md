---
title: 致命的なエラー C1099
ms.date: 11/04/2016
f1_keywords:
- C1099
helpviewer_keywords:
- C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
ms.openlocfilehash: 673a54f705a8ff46ad94167a4458ab538df69c88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387007"
---
# <a name="fatal-error-c1099"></a>致命的なエラー C1099

エディット コンティニュ エンジンはコンパイルを終了しています。

エディット コンティニュはコード変更をコンパイルする準備としてプリコンパイル済みヘッダー ファイルを読み込みましたが、その後のアクション (プリコンパイル済みヘッダーの `#include` ステートメントの前のコード変更、またはデバッガーの停止など) により、エディット コンティニュはこのプロセスでコンパイルを完了できませんでした。 このエラーを解決するために操作を実行する必要はありません。