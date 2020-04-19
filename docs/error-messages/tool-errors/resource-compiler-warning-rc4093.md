---
title: リソース コンパイラの警告 RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 23bf436e6e8338f89bc576564181c84715028332
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346211"
---
# <a name="resource-compiler-warning-rc4093"></a>リソース コンパイラの警告 RC4093

アクティブでないコード内の文字定数のエスケープ解除された改行

定数式、 `#if`、 `#elif`、 **#ifdef**、または **#ifndef**プリプロセッサ ディレクティブが 0 の場合、コードを作成するために評価が非アクティブに従います。 改行文字は、非アクティブなコード内で単一引用符または二重引用符のセット内で表示されます。

[次へ] の二重引用符までのすべてのテキストは、文字定数内にあると見なされていました。