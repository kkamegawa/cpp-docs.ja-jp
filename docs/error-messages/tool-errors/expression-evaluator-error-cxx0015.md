---
title: 式エバリュエーター エラー CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: f73aef18563426d28a81b92b3c37d1b7e345d0d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397147"
---
# <a name="expression-evaluator-error-cxx0015"></a>式エバリュエーター エラー CXX0015

式が複雑すぎます (スタック オーバーフロー)

入力された式は複雑すぎるか、C の式エバリュエーターを使用可能なストレージ量レベルが深すぎます入れ子になったでした。

通常、オーバーフローは、保留中の多数の計算のために発生します。

他の部分式を計算するを待機する必要がなくが見つかると、式の各コンポーネントを評価できるように、式のレイアウトを変更します。

複数のコマンド、式に分割します。

このエラーは、can0015 と同じものと同じです。