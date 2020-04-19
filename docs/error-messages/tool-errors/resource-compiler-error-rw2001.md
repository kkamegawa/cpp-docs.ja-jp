---
title: リソース コンパイラ エラー RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 4d298cdd9d96c55f283ce7f0e2ba04dd664941f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226507"
---
# <a name="resource-compiler-error-rw2001"></a>リソース コンパイラ エラー RW2001

前処理済みの RC ファイルに無効なディレクティブ

RC ファイルが含まれています、 **#pragma**ディレクティブ。

使用して、 **#ifndef**プリプロセッサ ディレクティブ、 **RC_INVOKED**インクルード ファイルを処理する際、リソース コンパイラを定義する定数。 場所、 **#pragma**ディレクティブでないコードのブロック内で処理されるときに、 **RC_INVOKED**定数が定義されます。 C と C++ コンパイラでのみ、リソース コンパイラではなく、ブロック内のコードが処理されます。 次のサンプル コードでは、この手法を示します。

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**プリプロセッサ ディレクティブ意味がない、です。RC ファイルです。 **#Include**プリプロセッサ ディレクティブで頻繁に使用します。ヘッダー ファイル (プロジェクト ベースのカスタム ヘッダー ファイルまたはその製品のいずれかで、Microsoft によって提供される標準のヘッダー ファイル) を含める RC ファイルです。 これらのいくつかのインクルード ファイルが含まれて、 **#pragma**ディレクティブ。 ヘッダー ファイルは、1 つまたは複数の他のヘッダー ファイル、問題のあるを含むファイルを含めることができますので **#pragma**ディレクティブを簡単にすぐにできない可能性があります。

**#Ifndef RC_INVOKED**プロジェクト ベースのヘッダー ファイル内のヘッダー ファイルなどの手法を制御できます。