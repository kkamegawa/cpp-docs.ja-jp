---
title: コンパイラ エラー C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: 2a76ecaf78b117b0c1acabd9fcd50c9ae0f73b98
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332063"
---
# <a name="compiler-error-c2338"></a>コンパイラ エラー C2338

> *エラー メッセージ*

このエラーは、によって発生することができます、`static_assert`コンパイル中にエラー。 によって、メッセージが提供される、`static_assert`パラメーター。

このエラー メッセージは、コンパイラに外部プロバイダーによっても生成できます。 ほとんどの場合、これらのエラーは、属性プロバイダー ATLPROV などの DLL によって報告されます。 このメッセージのいくつかの一般的な形式は次のとおりです。

- '*属性*' Atl 属性プロバイダー: エラー ATL*数* *メッセージ*

- 属性の使用法が正しくない '*属性*'

- '*使用状況*': 属性 'usage' の形式が正しくありません

これらのエラーでは、多くの場合、回復可能ではなく、コンパイラの致命的なエラーが続きます。

これらの問題を解決するには、属性の使用方法を修正します。 たとえば、場合によっては、使用する前になる属性パラメーターを宣言する必要があります。 ATL のエラー番号が指定されている場合より具体的な情報は、このエラーは、ドキュメントを確認します。
