---
title: プロジェクト ビルド エラー PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: 7c078a3d2aef24df9151cb10f81c1b7423809e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347588"
---
# <a name="project-build-error-prj0034"></a>プロジェクト ビルド エラー PRJ0034

プロジェクト レベルのカスタムの追加の依存関係 ' プロパティはビルドに含まれる手順 'macro' と 'macro_expansion' を評価します。

プロジェクトでカスタム ビルド ステップには、おそらくマクロ評価の問題により、追加の依存関係のエラーが含まれています。 このエラーにあるパス形式が正しくない、文字またはファイル パスでは無効な文字の組み合わせを含むもします。

このエラーを解決するのには、マクロを修正するか、パスの指定を修正します。 パスには、プロジェクト ディレクトリからの絶対パスを指定します。