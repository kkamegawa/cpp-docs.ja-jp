---
title: '/実験的: プリプロセッサ (プリプロセッサ準拠モードの有効化)'
description: '標準準拠プリプロセッサの実験的なコンパイラサポートを有効にするには、/実験的: プリプロセッサコンパイラオプションを使用します。'
ms.date: 10/31/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: cb1ac63d2c12083975139455d8625544cb419adf
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754044"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/実験的: プリプロセッサ (プリプロセッサ準拠モードの有効化)

このオプションを使用すると、C99 プリプロセッサ機能を含む、C++ 11 標準により厳密に準拠する実験的なトークンベースプリプロセッサが有効になります。 詳細については、「 [MSVC 実験的なプリプロセッサの概要](../../preprocessor/preprocessor-experimental-overview.md)」を参照してください。

## <a name="syntax"></a>構文

> **/実験的: プリプロセッサ**[ **-** ]

## <a name="remarks"></a>Remarks

試験的準拠プリプロセッサを有効にするには、 **/実験的: プリプロセッサ**コンパイラオプションを使用します。 従来のプリプロセッサを明示的に指定するには、**実験的なプリ**プロセッサオプションを使用します。

**/実験的: プリプロセッサ**オプションは、Visual Studio 2017 バージョン15.8 以降で使用できます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[追加オプション]** プロパティを変更して、 **/実験的: プリプロセッサ**を追加し、[ **OK]** を選択します。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)
