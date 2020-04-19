---
title: リソース コンパイラ エラー RC2101
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 595e87b73d79a01993e0e9b3aaa814332b21413f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345286"
---
# <a name="resource-compiler-error-rc2101"></a>リソース コンパイラ エラー RC2101

前処理済みの RC ファイルに無効なディレクティブ

リソース コンパイラのファイルが含まれています、 **#pragma**ディレクティブ。

使用して、 **#ifndef**インクルード ファイルを処理する際、リソース コンパイラを定義する RC_INVOKED 定数とプリプロセッサ ディレクティブです。 場所、 **#pragma** RC_INVOKED 定数が定義されている場合に処理されていないコードのブロック内のディレクティブ。 C と C++ コンパイラでのみ、リソース コンパイラではなく、ブロック内のコードが処理されます。 次のサンプル コードでは、この手法を示します。

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**プリプロセッサ ディレクティブ意味がない、です。RC ファイルです。 **#Include**プリプロセッサ ディレクティブで頻繁に使用します。ヘッダー ファイル (プロジェクト ベースのカスタム ヘッダー ファイルまたはその製品のいずれかで、Microsoft によって提供される標準のヘッダー ファイル) を含める RC ファイルです。 これらのいくつかのインクルード ファイルが含まれて、 **#pragma**ディレクティブ。 ヘッダー ファイルは、1 つまたは複数の他のヘッダー ファイル、問題のあるを含むファイルを含めることができますので **#pragma**ディレクティブを簡単にすぐにできない可能性があります。

**#Ifndef**プロジェクト ベースのヘッダー ファイル内のヘッダー ファイルを含む RC_INVOKED 手法を制御できます。