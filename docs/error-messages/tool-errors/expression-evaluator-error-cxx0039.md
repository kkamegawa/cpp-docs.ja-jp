---
title: 式エバリュエーター エラー CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 053e57a21f0cb75cbd96732edb6812b3557bcd50
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396978"
---
# <a name="expression-evaluator-error-cxx0039"></a>式エバリュエーター エラー CXX0039

シンボルがあいまいです。

C の式エバリュエーターでは、式で使用するシンボルのどのインスタンスを特定できません。 シンボルは、継承ツリー内で複数回に発生します。

スコープ解決演算子を使用する必要があります (`::`)、式で使用するインスタンスを明示的に指定します。

このエラーは、can0039 と同じものと同じです。