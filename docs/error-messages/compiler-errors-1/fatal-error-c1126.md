---
title: 致命的なエラー C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230013"
---
# <a name="fatal-error-c1126"></a>致命的なエラー C1126

'identifier': 自動メモリ割り当てサイズを超えています

関数 (とスワップ可能な関数の追加の 20 バイトなど、コンパイラによって使用される領域量が制限されています) のローカル変数に割り当てられた領域を超えています。

このエラーを修正するには使用`malloc`または`new`大量のデータを割り当てることです。