---
title: /volatile (volatile キーワードの解釈を)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 02871622242930d7419fda16f4d106fccb2056f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316640"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (volatile キーワードの解釈を)

指定する方法、[揮発性](../../cpp/volatile-cpp.md)キーワードの解釈します。

## <a name="syntax"></a>構文

> **/volatile:**{**iso**|**ms**}

## <a name="arguments"></a>引数

**/volatile:iso**<br/>
ISO 標準の C++ 言語で定義されている、厳密な `volatile` のセマンティックスを選択します。 volatile アクセスでは取得と開放のセマンティックスは保証されていません。 コンパイラが ARM をターゲットとする場合は、これは `volatile` の既定の解釈です。

**/volatile:ms**<br/>
Microsoft 拡張 `volatile` セマンティクスを選択すると、ISO 標準 C++ 言語を超えることを保証するメモリ オーダリングが追加されます。 volatile アクセスでは取得と開放のセマンティックスは保証されます。 ただし、このオプションにより、コンパイラはハードウェアのメモリ バリアを強制的に生成します。これによって ARM および他のメモリ オーダリングの弱いアーキテクチャでは、著しいオーバーヘッドが追加される場合があります。 コンパイラが ARM 以外のプラットフォームをターゲットとする場合は、これは `volatile` の既定の解釈です。

## <a name="remarks"></a>Remarks

使用することを強くお勧め **/volatile:iso**明示的な同期プリミティブやスレッド間で共有されているメモリを扱うときのコンパイラ組み込みと共にします。 詳細については、次を参照してください。[揮発性](../../cpp/volatile-cpp.md)します。

既存のコードを移植したり、プロジェクトの途中でこのオプションを変更した場合は、警告を有効にする時間が立つ可能性[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)セマンティクスの違いによって影響を受けるコードの場所を識別します。

`#pragma` には、このオプションを制御するための相当するものはありません。

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>/volatile コンパイラ オプションを Visual Studio で設定するには

1. 開く、**プロパティ ページ**プロジェクトのダイアログ ボックス。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. **追加オプション**ボックスで、追加 **/volatile:iso**または **/volatile:ms**選び、 **OK**または**適用** 、変更を保存します。

## <a name="see-also"></a>関連項目

[volatile](../../cpp/volatile-cpp.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
