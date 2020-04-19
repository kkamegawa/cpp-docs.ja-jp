---
title: プロジェクト ビルド エラー PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: f1f292f3979c993a8fa8cb8ff44653ac7124b121
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344356"
---
# <a name="project-build-error-prj0032"></a>プロジェクト ビルド エラー PRJ0032

プロジェクト レベルのカスタム ビルド ステップに 'Outputs' プロパティには、評価を出す 'macro_expansion' の ' macro' が含まれています。

プロジェクトでカスタム ビルド ステップでは、おそらくマクロ評価の問題により、不正な出力がありました。 このエラーにあるパス形式が正しくない、文字またはファイル パスでは無効な文字の組み合わせを含むもします。

このエラーを解決するのには、マクロを修正するか、パスの指定を修正します。 パスには、プロジェクト ディレクトリからの絶対パスを指定します。