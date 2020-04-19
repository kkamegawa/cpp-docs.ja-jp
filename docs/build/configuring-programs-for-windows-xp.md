---
title: Windows XP 用プログラムの構成
ms.date: 05/16/2019
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 55753737b4868f33487ed980eaf37a8801f59638
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450702"
---
# <a name="configuring-programs-for-windows-xp"></a>Windows XP 用プログラムの構成

Visual Studio は複数のプラットフォーム ツールセットをサポートしているため、既定のツールセットでサポートされていないオペレーティング システムとランタイム ライブラリに対応することができます。 たとえば、プラットフォーム ツールセットを切り替えることで、Visual Studio の MSVC コンパイラでサポートされている C++11、C++14、C++17 言語拡張を使用し、Windows XP と Windows Server 2003 を対象にするアプリを作成できます。 また、以前のプラットフォーム ツールセットを使用して、バイナリ互換性のあるレガシ コードを保守しながら、Visual Studio IDE の最新の機能も利用できます。

Visual Studio 2019 以降では、v142 ツールセットを使用した Windows XP 用のコードの作成はサポートされていません。 Visual Studio 2017 に付属している v141 ツールセットを使用した Windows XP の開発のサポートは、Visual Studio インストーラーでオプションのコンポーネントとして入手できます。

## <a name="install-the-windows-xp-platform-toolset"></a>Windows XP プラットフォーム ツールセットのインストール

Visual Studio 2017 で Windows XP と Windows Server 2003 を対象にするプラットフォーム ツールセットとコンポーネントを取得するには、Visual Studio インストーラーを実行します。 Visual Studio を初めてインストールするとき、あるいは **[変更]** を選択して既存のインストールを変更するとき、 **[C++ によるデスクトップ開発]** ワークロードを必ず選択します。 このワークロードのオプション コンポーネントの一覧で、 **[C++ に関する Windows XP サポート]** を選択し、 **[インストール]** または **[変更]** を選択します。

## <a name="windows-xp-targeting-experience"></a>Windows XP 対応のエクスペリエンス

Visual Studio に含まれている Windows XP プラットフォーム ツールセットは Windows 7 SDK のバージョンの 1 つですが、現行の C++ コンパイラが使用されています。 また、これは、プロジェクトのプロパティを適切な既定値に構成します。たとえば、下位レベルへの対応用の、互換性のあるリンカーの仕様などです。 Windows XP プラットフォーム ツールセットを使用して作成された Windows デスクトップ アプリのみが Windows XP と Windows Server 2003 で動作しますが、これらのアプリは、最近の Windows オペレーティング システムでも動作します。

#### <a name="to-target-windows-xp"></a>Windows XP に対応するには

1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択します。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスにある **[構成プロパティ]** の **[全般]** で、 **[プラットフォーム ツールセット]** プロパティを必要な Windows XP ツールセットに設定します。 たとえば、Visual Studio 2017 の Microsoft C++ コンパイラを使用し、Windows XP および Windows Server 2003 向けのコードを作成するには、 **[Visual Studio 2017 - Windows XP (v141_xp)]** を選択します。

### <a name="c-runtime-support"></a>C++ ランタイムのサポート

Windows XP のプラットフォーム ツールセットの他に、C ランタイム ライブラリ (CRT)、C++ 標準ライブラリ、Active Template Library (ATL)、同時実行ランタイム ライブラリ (ConCRT)、並列パターン ライブラリ (PPL)、Microsoft Foundation Class ライブラリ (MFC)、C++ AMP (C++ Accelerated Massive Programming) ライブラリに Windows XP と Windows Server 2003 のランタイム サポートが含まれます。 これらのオペレーティング システムでサポートされる最小バージョンは、x86 用 Windows XP Service Pack 3 (SP3)、x64 用 Windows XP Service Pack 2 (SP2)、x86 と x64 用 Windows Server 2003 Service Pack 2 (SP2) です。

これらのライブラリは Visual Studio によってインストールされているプラットフォーム ツールセットによりサポートされますが、サポート状況はターゲットに応じて異なります。

|ライブラリ|Windows デスクトップ アプリを対象とする既定のプラットフォーム ツールセット|Store アプリを対象とする既定のプラットフォーム ツールセット|Windows XP と Windows Server 2003 を対象とする Windows XP プラットフォーム ツールセット|
|---|---|---|---|
|CRT|X|X|x|
|C++ 標準ライブラリ|x|X|X|
|[ATL]|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|x||

> [!NOTE]
> C++/CLI で作成され、.NET Framework 4 を対象とするアプリは、Windows XP と Windows Server 2003 で動作します。

### <a name="differences-between-the-toolsets"></a>ツールセットの間の相違点

プラットフォームとライブラリのサポートの違いにより、Windows XP のプラットフォーム ツールセットを使用するアプリの開発のエクスペリエンスは、既定の Visual Studio プラットフォーム ツールセットを使用するアプリの場合ほどに完全ではありません。

- **C++ 言語の機能**

   v110\_xp のプラットフォーム ツールセットを使用するアプリでサポートされているのは、Visual Studio 2012 に実装されている C++ 言語機能だけです。 v120\_xp のプラットフォーム ツールセットを使用するアプリでサポートされているのは、Visual Studio 2013 に実装されている C++ 言語機能だけです。 v140\_xp のプラットフォーム ツールセットを使用するアプリでサポートされているのは、Visual Studio 2015 に実装されている C++ 言語機能だけです。 Visual Studio は、以前のプラットフォーム ツールセットを使用してビルドするときに、対応するコンパイラを使用します。 そのバージョンのコンパイラに実装されている C++ 言語の追加機能を利用するには、より新しい Windows XP のプラットフォーム ツールセットを使用します。

- **リモート デバッグ**

   Remote Tools for Visual Studio は、Windows XP または Windows Server 2003 のリモート デバッグに対応していません。 Windows XP または Windows Server 2003 で実行しているときにアプリをデバッグするために、以前のバージョンの Visual Studio のデバッガーを使用し、ローカルまたはリモートでデバッグすることができます。 これと似ているのが Windows Vista のアプリのデバッグのエクスペリエンスであり、これはプラットフォーム ツールセットのランタイム ターゲットですが、リモートのデバッグ ターゲットではありません。

- **静的分析**

   Windows XP のプラットフォーム ツールセットは、Windows 7 SDK の SAL 注釈とランタイム ライブラリに互換性がないため、静的分析をサポートしていません。 Windows XP または Windows Server 2003 をサポートするアプリの静的分析を実行する場合は、既定のプラットフォーム ツールセットに対応するようソリューションを一時的に切り替え、分析を実行してから Windows XP のプラットフォーム ツールセットに戻ってアプリをビルドすることができます。

- **DirectX グラフィックスのデバッグ**

   グラフィックス デバッガーは Direct3D 9 API をサポートしていないため、Windows XP または Windows Server 2003 で Direct3D を使用するアプリのデバッグにこれを利用することはできません。 ただし、アプリが Direct3D 10 または Direct3D 11 の API を使用する代替のレンダラーを実装する場合、これらの API を使用する場合の問題の診断にグラフィックス デバッガーを利用できます。

- **HLSL の構築**

   既定では、Windows XP ツールセットでは HLSL のソース コード ファイルはコンパイルされません。 HLSL ファイルをコンパイルするには、June 2010 DirectX SDK をダウンロードしてインストールし、プロジェクトの VC ディレクトリに含めるように設定します。 詳細については、[June 2010 DirectX SDK ダウンロード ページ](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)の「DirectX SDK はインクルード/ライブラリ パスを Visual Studio 2010 に登録しない」セクションを参照してください。
