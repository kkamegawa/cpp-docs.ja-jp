---
title: ATL プロジェクトで CRT にリンクするには
ms.date: 11/04/2016
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
ms.openlocfilehash: e247897f42eea5b4ced5bc40b556137a1a5cd228
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261931"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>ATL プロジェクトで CRT にリンクするには

[C ランタイム ライブラリ](../c-runtime-library/crt-library-features.md)(CRT) はプログラミングがより簡単 ATL 開発中に多数の役立つ機能を提供します。 すべての ATL プロジェクトでは、CRT ライブラリにリンクします。 長所と短所のメソッドのリンクを確認できます[CRT へのリンクに使用されるメソッドの利点とトレードオフ](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)します。

## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>プログラム イメージの CRT へのリンクの効果

CRT に静的にリンクする場合は CRT からのコードは、実行可能イメージに配置され、イメージを実行するシステムで、CRT DLL に存在する必要はありません。 CRT に動的にリンクする場合、CRT DLL 内のコードへの参照は、イメージは、コード自体ではなくに配置されます。 イメージを特定のシステムで実行するためには、CRT DLL はそのシステムに存在する必要があります。 でもを動的にリンクする場合、CRT、いくつかのコードを静的にリンクできますがするあります (たとえば、 `DllMainCRTStartup`)。

イメージをリンクするときに明示的または暗黙的に指定する、オペレーティング システムは、イメージの読み込み後に呼び出すエントリ ポイント。 既定のエントリ ポイントは、dll の場合、`DllMainCRTStartup`します。 Exe`WinMainCRTStartup`します。 /ENTRY リンカー オプションを使用して既定をオーバーライドすることができます。 CRT の実装を提供する`DllMainCRTStartup`、 `WinMainCRTStartup`、および`wWinMainCRTStartup`(exe Unicode エントリ ポイント)。 これらの CRT で提供されるエントリ ポイントはグローバル オブジェクトのコンス トラクターを呼び出すし、一部の CRT 関数によって使用されるその他のデータ構造を初期化します。 このスタートアップ コードでは、静的にリンクされている場合に、約 25 K がイメージに追加します。 動的にリンクされている場合は、イメージのサイズを小さく抑えるため、コードのほとんどは、DLL 内です。

詳細については、リンカーのトピックを参照してください。 [/ENTRY (エントリ ポイント シンボル)](../build/reference/entry-entry-point-symbol.md)します。

## <a name="optimization-options"></a>最適化オプション

/OPT:NOWIN98 リンカー オプションを使用してさらに低下 10 k は、既定の ATL コントロール譲歩読み込み Windows 98 システム上の時間が増加します。 リンク オプションの詳細については、次を参照してください。 [/OPT (最適化)](../build/reference/opt-optimizations.md)します。

## <a name="see-also"></a>関連項目

[ATL および C ランタイム コードによるプログラミング](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL と Visual C++ ランタイム ライブラリの動作](../build/run-time-library-behavior.md)
