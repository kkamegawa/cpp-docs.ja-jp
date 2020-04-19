---
title: コンパイラ エラー C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 5730102371d00ebaf3ae05fdefb70184b58d7c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400332"
---
# <a name="compiler-error-c3505"></a>コンパイラ エラー C3505

> タイプ ライブラリを読み込むことができません '*guid*'

C3505 可能性があります、32 ビット、x86 でホストされているクロス コンパイラの 64 ビットを実行している場合は、x64 64 ビット上のターゲット コンピューターの WOW64 の下で、コンパイラが実行されているため、およびだけことができますが、32 ビット レジストリ ハイブから読み取る。

タイプ ライブラリをインポートしようとしての 32 ビットと 64 ビットの両方のバージョンを構築することにより、このエラーを解決し、両方を登録できます。  ネイティブの 64 ビットのコンパイラは、変更する必要がありますを使用することも、 **vc++ ディレクトリ**64 ビット コンパイラをポイントする IDE でのプロパティ。

詳細については、次のトピックを参照してください。

- [方法: 64 ビットの Visual C++ ツールセットをコマンド ラインから有効にする](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [方法: Visual C++ プロジェクトを 64 ビット、x64 プラットフォーム用に設定する](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)