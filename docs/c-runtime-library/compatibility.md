---
title: 互換性
description: Microsoft Universal C runtime library (UCRT) と標準 C ライブラリ、POSIX、安全な CRT、およびストアアプリの互換性について説明します。
ms.date: 12/06/2019
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: a3bc6f53d1c86268cae95e60a93576c4ac8e3e14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988732"
---
# <a name="compatibility"></a>互換性

Universal C Run-Time Library (UCRT) は、C++ に適合するために必要な C 標準ライブラリの大部分をサポートしています。 C99 (ISO/IEC 9899:1999) ライブラリを実装しています。ただし、\<> tgmath.h> に定義されている型汎用マクロと、\<の > で厳密な型の互換性があります。 UCRT は、POSIX の大規模なサブセットも実装します。 1 (ISO/IEC 9945-1:1996、POSIX システムアプリケーションプログラミングインターフェイス) C ライブラリ。 ただし、特定の POSIX 標準に完全に準拠しているわけではありません。 UCRT では、標準の一部ではないいくつかの Microsoft 固有の関数とマクロも実装されています。

Visual C++ の Microsoft による実装に固有の関数は vcruntime ライブラリ内にあります。  これらの関数の多くは内部使用用であり、ユーザーコードから呼び出すことはできません。 一部の関数は、デバッグでの使用や、実装の互換性の目的でドキュメントに記載されています。

C++ 標準では、グローバル名前空間のアンダースコアで始まる名前は、実装用に予約されています。 POSIX 関数と Microsoft 固有のランタイムライブラリ関数はどちらもグローバル名前空間にありますが、標準の C ランタイムライブラリの一部ではありません。 そのため、これらの関数の Microsoft の優先実装には、先頭にアンダースコアが付いています。 移植性の目的で、UCRT では既定の名前もサポートされていますが、それらを使用するコードがコンパイルされると、非推奨の警告が Microsoft C++ コンパイラから出されます。 既定の名前のみが非推奨とされます。関数自体ではありません。 この警告を表示しないようにするには、元の POSIX 名を使用するコードでヘッダーをインクルードする前に `_CRT_NONSTDC_NO_WARNINGS` を定義します。

標準 C ライブラリの関数の中には、パラメーターを誤用した場合やバッファーのチェックを行わない場合、安全に使用できないものがありました。 これらの関数は、多くの場合、コードのセキュリティ問題の発生源になります。 Microsoft では、パラメーターの使用法を確認するために、これらの関数の安全なバージョンのセットを作成しました。 実行時に問題が検出された場合は、無効なパラメーターハンドラーを呼び出します。  既定では、より安全で利用可能なバリアントが含まれる関数が使用されると、Microsoft C++ コンパイラから非推奨の警告が出されます。 としてC++コードをコンパイルするときに、ほとんどの警告を除去するために `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` を1として定義できます。 このマクロは、移植可能なソースコードを維持しながら、テンプレートのオーバーロードがより安全なバリアントを呼び出すことができるようにします。 この警告を表示しないようにするには、これらの関数を使用するコードでヘッダーをインクルードする前に `_CRT_SECURE_NO_WARNINGS` を定義します。 詳細については、「 [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md)」を参照してください。

特定の関数に関するドキュメントで別途説明されている場合を除き、UCRT は Windows API と互換性があります。  Windows ストアアプリまたはユニバーサル Windows プラットフォーム ([UWP](/uwp)) アプリでは、一部の関数はサポートされていません。 これらの関数は、「[ユニバーサル Windows プラットフォームアプリでサポートされていない CRT 関数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」に記載されています。

## <a name="related-articles"></a>関連トピック

|[タイトル]|説明|
|-----------|-----------------|
|[UWP アプリ、Windows ランタイム、および C ランタイム](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|UCRT ルーチンがユニバーサル Windows アプリまたは Microsoft Store アプリと互換性がない場合について説明します。|
|[ANSI C 準拠](../c-runtime-library/ansi-c-compliance.md)|UCRT における標準に適合した名前付けについて説明します。|
|[UNIX](../c-runtime-library/unix.md)|プログラムを UNIX に移植するためのガイドラインを提供します。|
|[Windows プラットフォーム (CRT)](../c-runtime-library/windows-platforms-crt.md)|CRT がサポートするオペレーティング システムの一覧を示します。|
|[下位互換性](../c-runtime-library/backward-compatibility.md)|CRT の古い名前が新しい名前にマップされる方法について説明します。|
|[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)|CRT ライブラリ (.lib) ファイルと、関連するコンパイラ オプションの概要を示します。|