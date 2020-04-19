---
title: ガイド付き最適化のプロファイルの環境変数
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195274"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>ガイド付き最適化のプロファイルの環境変数

作成されたイメージのテスト シナリオに影響する 3 つの環境変数がある **/LTCG:PGI**プロファイル ガイド付き最適化の。

- **PogoSafeMode**アプリケーションのプロファイリングに高速モードとセーフ モードを使用するかどうかを指定します。

- **VCPROFILE_ALLOC_SCALE**プロファイラーで使用するための追加のメモリを追加します。

- **VCPROFILE_PATH** .pgc ファイルを使用するフォルダーを指定することができます。

**PogoSafeMode と VCPROFILE_ALLOC_SCALE 環境変数は、Visual Studio 2015 以降では非推奨します。** リンカー オプション[/GENPROFILE または/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)と[/USEPROFILE](reference/useprofile.md)これらの環境変数として同じリンカーの動作を指定します。

## <a name="pogosafemode"></a>PogoSafeMode

この環境変数が非推奨とされます。 使用して、 **EXACT**または**noexact は、** 引数 **/GENPROFILE**または **/FASTGENPROFILE**この動作を制御します。

設定またはオフ、 **PogoSafeMode** x86 上でアプリケーションのプロファイリングに高速モードとセーフ モードを使用するかどうかを指定する環境変数のシステム。

最適化のガイド付きプロファイル (PGO) が、プロファイリング フェーズ中に 2 つのモードを持つ:*高速モード*と*セーフ モード*します。 使用して高速モードでプロファイリングを行う、ときに、 **INC**命令データ カウンター数を増やします。 **INC**命令は高速化が、スレッド セーフではありません。 セーフ モードでプロファイリングを行う、ときに使用して、 **LOCK INC**命令データ カウンター数を増やします。 **LOCK INC**命令と同じ機能を持つ、 **INC**よりも低速ですが、命令があり、スレッド セーフで、 **INC**命令。

既定では、PGO プロファイリングは高速モードで動作します。 **PogoSafeMode**がセーフ モードを使用するかどうかにのみ必要です。

セーフ モードでの PGO プロファイリングを実行する、環境変数を使用する必要がありますか**PogoSafeMode**かリンカー スイッチ **/PogoSafeMode**、システムによって異なります。 x64 コンピューターでプロファイリングを実行する場合は、リンカー スイッチを使用する必要があります。 X86 でプロファイリングを実行するかどうか、コンピューター、リンカーを使用することがあります切り替えるか、設定、 **PogoSafeMode**最適化プロセスを開始する前に、任意の値を環境変数。

### <a name="pogosafemode-syntax"></a>PogoSafeMode 構文

> **set PogoSafeMode**[**=**_value_]

設定**PogoSafeMode**セーフ モードを有効にする任意の値にします。 前の値をクリアして、高速モードを再度有効にする値を設定します。

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

この環境変数が非推奨とされます。 使用して、 **MEMMIN**と**MEMMAX**引数 **/GENPROFILE**または **/FASTGENPROFILE**この動作を制御します。

変更、 **VCPROFILE_ALLOC_SCALE**プロファイル データを保持するメモリの量を変更する環境変数が割り当てられます。 まれなケースではありません十分なメモリをサポートするために使用可能なテスト シナリオを実行するときに、プロファイル データを収集します。 その場合、メモリの量を増やすを設定して**VCPROFILE_ALLOC_SCALE**します。 不足しているメモリがあることを示すテストの実行中にエラー メッセージを受信する場合に大きな値を割り当てる**VCPROFILE_ALLOC_SCALE**まで、メモリ不足のエラーのない完全なテストを実行します。

### <a name="vcprofileallocscale-syntax"></a>VCPROFILE_ALLOC_SCALE 構文

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value*パラメーターは、テスト シナリオの実行対象とするメモリの量のスケール ファクター。  既定値は 1 です。 たとえば、このコマンドラインは、2 にスケール ファクターを設定します。

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

使用して、 **VCPROFILE_PATH** .pgc ファイルを作成するディレクトリを指定する環境変数。 既定では、.pgc ファイルは、プロファイリング中、バイナリと同じディレクトリに作成されます。 ただし、バイナリの絶対パスが存在しない場合、バイナリがビルドされた場所から別のコンピューターにプロファイルのシナリオを実行すると、大文字と小文字をすることがある、設定できます**VCPROFILE_PATH**ターゲット コンピューター上に存在するパスにします。

### <a name="vcprofilepath-syntax"></a>VCPROFILE_PATH 構文

> **set VCPROFILE_PATH**[**=**_path_]

設定、*パス*.pgc ファイルを追加するディレクトリ パスのパラメーター。 たとえば、このコマンドラインは、C:\profile にフォルダーを設定します。

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>関連項目

[ガイド付き最適化のプロファイル](profile-guided-optimizations.md)<br/>
[/GENPROFILE と/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
