---
title: ワイルドカード引数の展開
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: f1fb964fe98223fb7187b83c7101027ed1f9cbea
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149051"
---
# <a name="expanding-wildcard-arguments"></a>ワイルドカード引数の展開

**Microsoft 固有の仕様**

C プログラムを実行する際、コマンド ラインのファイル名引数とパス引数の指定に、2 つのワイルドカード (疑問符 (?) およびアスタリスク (*)) のいずれかを使用できます。

既定では、ワイルドカードはコマンドラインの引数では展開されません。 setargv.obj または wsetargv.obj ファイルとリンクしてワイルドカードを展開し、標準の引数ベクターの `argv` 読み込みルーチンをワイルドカードを展開するバージョンと置き換えることができます。 プログラムが `main` 関数を使用している場合は、setargv.obj とリンクします。プログラムが `wmain` 関数を使用している場合は、wsetargv.obj とリンクします。これら両方の動作は同等です。

setargv.obj または wsetargv.obj とリンクするには、 **/link** オプションを使用します。 次に例を示します。

**cl example.c /link setargv.obj**

ワイルドカードはオペレーティング システム コマンドと同じように展開されます (ワイルドカードの使用経験がない場合は、オペレーティング システムのユーザー ガイドを参照)。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[リンク オプション](../c-runtime-library/link-options.md)<br/>
[main 関数とプログラム実行](../c-language/main-function-and-program-execution.md)
