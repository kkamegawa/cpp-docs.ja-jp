---
title: コンパイラ エラー C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375913"
---
# <a name="compiler-error-c3550"></a>コンパイラ エラー C3550

このコンテキストでは単純な 'decltype(auto)' のみが許可されます

`decltype(auto)` を関数の戻り値の型のプレースホルダーとして使用する場合は、単独で使用する必要があります。 ポインターの宣言 (`decltype(auto*)`)、参照の宣言 (`decltype(auto&)`)、またはその他の修飾の一部として使用することはできません。

## <a name="see-also"></a>関連項目

[auto](../../cpp/auto-cpp.md)