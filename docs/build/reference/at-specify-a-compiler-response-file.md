---
title: '@ (コンパイラ応答ファイルの指定)'
ms.date: 11/04/2016
f1_keywords:
- '@'
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
ms.openlocfilehash: c2b5578e1ce1db590bdf5abbff0c91e858803ad7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273002"
---
# <a name="-specify-a-compiler-response-file"></a>@ (コンパイラ応答ファイルの指定)

コンパイラ応答ファイルを指定します。

## <a name="syntax"></a>構文

> **\@**<em>response_file</em>

## <a name="arguments"></a>引数

*response_file*<br/>
コンパイラのコマンドを含むテキスト ファイル。

## <a name="remarks"></a>Remarks

応答ファイルは、コマンドラインで指定する任意のコマンドを含めることができます。 コマンドライン引数は、127 文字を超えた場合に便利なことができます。

指定することはできません、 **\@** から応答ファイル内のオプションします。 つまり、応答ファイルには、別の応答ファイルを埋め込むことはできません。

コマンドラインから多くの応答ファイル オプションを指定できます (たとえば、 `@respfile.1 @respfile.2`) します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

- 応答ファイルは、開発環境内から指定することはできませんし、コマンドラインで指定する必要があります。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- このコンパイラ オプションをプログラムで変更することはできません。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
