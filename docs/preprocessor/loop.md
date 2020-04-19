---
title: loop プラグマ
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: 013540ffe120f42c15538ce86661753b9cf9416f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220848"
---
# <a name="loop-pragma"></a>loop プラグマ

ループコードが自動並行化によってどのように見なされるかを制御します。または、自動ベクター化によって考慮されないループを除外します。

## <a name="syntax"></a>構文

> **#pragma ループ (hint_parallel (** *n* **))** \
> **#pragma ループ (no_vector)** \
> **#pragma ループ (ivdep)**

### <a name="parameters"></a>パラメーター

**hint_parallel (** *n* **)** \
*N*スレッド間でこのループを並列化する必要があることをコンパイラにヒントします。 *n*は、正の整数リテラルまたは0です。 *N*が0の場合、スレッドの最大数が実行時に使用されます。 これは、コマンドではなく、コンパイラに対するヒントです。 ループが並列化される保証はありません。 ループにデータの依存関係または構造上の問題がある場合は、並列化されません。 たとえば、ループ本体の外で使用されるスカラーに格納する場合は、並列化されません。

コンパイラは、 [/Qpar](../build/reference/qpar-auto-parallelizer.md)コンパイラスイッチが指定されていない限り、このオプションを無視します。

**no_vector**\
既定では、自動ベクター化は、評価されたすべてのループのベクター化を試行することができます。 次のループの自動ベクター化を無効にするには、このプラグマを指定します。

**ivdep**\
このループのベクター依存関係を無視するためのヒント。 このオプションを**hint_parallel**と共に使用します。

## <a name="remarks"></a>Remarks

**Loop**プラグマを使用するには、ループの定義の直前に配置します。 プラグマは後続のループのスコープ内で有効です。 1 つのループに複数のプラグマを任意の順序で適用できますが、プラグマを 1 つずつ個別のステートメントで指定する必要があります。

## <a name="see-also"></a>関連項目

[自動並列化と自動ベクター化](../parallel/auto-parallelization-and-auto-vectorization.md)\
[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
