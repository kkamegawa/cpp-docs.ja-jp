---
title: リンカー ツールの警告 LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: c6a5a0714e070e6cf3aee8efcdfbdfa07fa9ee69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399935"
---
# <a name="linker-tools-warning-lnk4086"></a>リンカー ツールの警告 LNK4086

エントリ ポイント 'function' は 'number' バイトの引数を持つ _ _stdcall ではありません。イメージは動作しない可能性があります。

DLL のエントリ ポイントである必要があります`__stdcall`します。 使用して、関数を再コンパイルするか、 [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)オプションまたは指定`__stdcall`または WINAPI 関数を定義するときにします。