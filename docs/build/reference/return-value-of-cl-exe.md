---
title: cl.exe の戻り値
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 1617208a8d99e3c5643330f75faf9beed9ce5f1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319019"
---
# <a name="return-value-of-clexe"></a>cl.exe の戻り値

cl.exe では、動作が正常終了した場合 (エラーがない場合) は 0 を返し、それ以外の場合は 0 以外の値を返します。

スクリプト、PowerShell、.cmd、または .bat ファイルからコンパイルを行う場合は、cl.exe の戻り値が役に立ちます。 エラーまたは警告が発生した場合にそれらを解決できるように、コンパイラの出力をキャプチャすることをお勧めします。

cl.exe のエラー終了コードは多すぎて、すべてを表示することはできません。 Winerror.h で、エラー コードを調べることができます、キットの %programfiles (x86) %\Windows % では、Windows Software Development Kit に含まれる ntstatus.h ファイルまたは\\<em>バージョン</em>\Include\shared\ ディレクトリにします。 10 進数で返されるエラー コードは、16 進数に変換して検索する必要があります。 たとえば、16 進数に変換された -1073741620 エラー コードは 0xC00000CC です。 このエラーは ntstatus.h にあり、対応するメッセージは "指定した共有名がリモート サーバーで見つかりません" です。 Windows エラー コードのダウンロード可能な一覧は、次を参照してください[ &#91;MS ERREF&#93;:。Windows エラー コード](https://msdn.microsoft.com/library/cc231196)します。

Visual Studio でエラー ルックアップ ユーティリティを使用して、コンパイラ エラー メッセージの意味を検索することもできます。 Visual Studio コマンド シェルで次のように入力します。 **errlook.exe**ユーティリティを起動します。 または、メニュー バーで、Visual Studio IDE で選択する**ツール**、**エラー ルックアップ**します。 エラー値を入力して、そのエラーに関連付けられている説明のテキストを見つけます。 詳細については、次を参照してください。 [ERRLOOK リファレンス](errlook-reference.md)します。

## <a name="remarks"></a>Remarks

次に、cl.exe の戻り値を使用するサンプル .bat ファイルを示します。

```cmd
echo off
cl /W4 t.cpp
@if ERRORLEVEL == 0 (
   goto good
)

@if ERRORLEVEL != 0 (
   goto bad
)

:good
   echo "clean compile"
   echo %ERRORLEVEL%
   goto end

:bad
   echo "error or warning"
   echo %ERRORLEVEL%
   goto end

:end
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
