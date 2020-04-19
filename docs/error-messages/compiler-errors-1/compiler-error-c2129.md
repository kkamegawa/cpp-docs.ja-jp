---
title: コンパイラ エラー C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: e55107419235420d272c738e9d8ef7cf277c11c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397628"
---
# <a name="compiler-error-c2129"></a>コンパイラ エラー C2129

静的関数 'function' が宣言されていますが、定義されていません

前方参照される、`static`定義されていない関数です。

A`static`ファイルのスコープ内で関数を定義する必要があります。 宣言する必要があります、関数は、別のファイルで定義されているが場合、`extern`します。