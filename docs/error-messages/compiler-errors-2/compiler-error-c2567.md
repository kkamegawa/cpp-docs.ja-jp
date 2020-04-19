---
title: コンパイラ エラー C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: eec529f43e23810843651888ef5722c5d0a0b2c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366356"
---
# <a name="compiler-error-c2567"></a>コンパイラ エラー C2567

'file' のメタデータを開くことができません、ファイルが削除されたか移動

ソースで参照されたメタデータ ファイル (と`#using`) が見つかりませんでした同じディレクトリにコンパイラのバック エンドのプロセスによって、コンパイラ フロント エンドのプロセスであったためです。 参照してください[#using ディレクティブ](../../preprocessor/hash-using-directive-cpp.md)詳細についてはします。

使用してコンパイルする場合に C2567 が考えられます **/c**いずれかでコンピューターし、別のコンピューター上のリンク時コード生成を試みます。 詳細については、次を参照してください。 [/LTCG (リンク時コード生成)](../../build/reference/ltcg-link-time-code-generation.md))。

コンピューターのメモリ不足であることを示すも可能性があります。

このエラーを修正するには、ビルド プロセスのすべてのフェーズのメタデータ ファイルは同じディレクトリの場所にいることを確認します。