---
title: '#ifdef および #ifndef ディレクティブ (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: 433076388f3646b19d75a907c6b2254098096688
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220105"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef ディレクティブと #ifndef ディレクティブ (CC++/)

**#Ifdef**ディレクティブと **#ifndef**ディレクティブは、**定義さ**れた演算子と共に使用する場合、 [#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)ディレクティブと同じ効果があります。

## <a name="syntax"></a>構文

> **#ifdef** *識別子*\
> **#ifndef** *識別子*

これらのディレクティブは次のようになります。

> **#if 定義済み** *識別子*\
> **#if! が定義されました** *識別子*

## <a name="remarks"></a>Remarks

任意の場所`#if`で使用できる **#ifdef**ディレクティブと **#ifndef**ディレクティブを使用できます。 識別子が定義されている`#if 1`場合 、 **#ifdef** *識別子*ステートメントはと同じです。 これは、*識別子*が定義されていない`#undef` `#if 0`場合、またはディレクティブによって定義されていない場合と同じです。 これらのディレクティブは、C または C++ ソース コードで宣言された識別子ではなく、`#define` で定義された識別子の有無を調べます。

これらのディレクティブは、言語の以前のバージョンとの互換性を維持するために用意されています。 `#if`ディレクティブで使用される**定義済み (** *識別子* **)** 定数式が推奨されます。

**#Ifndef**ディレクティブは、 **#ifdef**によってチェックされる条件の反対を確認します。 識別子が定義されていない場合、または定義がで`#undef`削除されている場合、条件は true (0 以外) になります。 それ以外の場合、条件は False (0) です。

**Microsoft 固有の仕様**

この*識別子*は、コマンドラインから[/d](../build/reference/d-preprocessor-definitions.md)オプションを使用して渡すことができます。 では、最大30個の`/D`マクロを指定できます。

**#Ifdef**ディレクティブは、定義が存在するかどうかを確認する場合に役立ちます。これは、コマンドラインから定義を渡すことができるためです。 例えば:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)
