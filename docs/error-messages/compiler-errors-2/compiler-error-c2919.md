---
title: コンパイラ エラー C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: ab11226c8cc4629a265dd182d5f882f6b3be7e5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160856"
---
# <a name="compiler-error-c2919"></a>コンパイラ エラー C2919

' type':WinRT 型の発行サーフェスで演算子を使用することはできません。

Windows ランタイムの型システムでは、型の発行サーフェスで演算子メンバー関数をサポートしていません。 これは、すべての言語で演算子メンバー関数を使用できるとは限らないためです。 同じクラスまたはコンパイル ユニット内に、C++ コードから呼び出されるプライベートまたは内部の演算子メンバー関数を作成できます。

この問題を解決するには、演算子メンバー関数をパブリック インターフェイスから削除するか、名前付きのメンバー関数に変更します。 たとえば、`operator==` の代わりに、メンバー関数に `Equals` という名前を付けます。