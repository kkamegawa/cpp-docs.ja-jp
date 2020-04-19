---
title: ガイド付き最適化のプロファイルのエラー PG0165
description: ガイド付き最適化 (PGO) データの読み取りプロファイルでの PG0165 エラーについて説明します。
ms.date: 10/30/2019
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: c5e5c5d37f8c70a6c2a3d9f7a43c13bb46d0e25a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626804"
---
# <a name="profile-guided-optimization-error-pg0165"></a>ガイド付き最適化のプロファイルのエラー PG0165

ガイド付き最適化のプロファイルデータの読み取り中にエラーが発生しました。 このエラーは、次のいくつかの形式で表示されます。

> '*Filename*' を読み取っています: ' pgd バージョンはサポートされていません (バージョンが一致しません) '。

PGD ファイルは、特定のコンパイラツールセットに固有のものです。 このエラーは、*ファイル名*を作成するために使用したものとは異なるコンパイラを使用している場合に生成されます。 このエラーは、このコンパイラツールセットが、現在のプログラムを最適化するために、*ファイル名 .pgd*のデータを使用できないことを示しています。 この問題を解決するには、現在のコンパイラツールセットを使用して、*ファイル名*を再生成します。

> '*Filename. .pgd*' を読み取っています: ' pgd ファイルは読み取り専用です。 '。

このエラーは、ファイルシステムで PGD ファイルが読み取り専用としてマークされている場合に表示されます。 この問題を解決するには、ファイル属性を読み取り/書き込みに変更します。
