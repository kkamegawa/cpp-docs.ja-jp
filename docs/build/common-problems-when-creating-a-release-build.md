---
title: リリース ビルド作成時によくある問題
ms.date: 11/04/2016
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 5372fe4e96c444d454c277394dd811cfac14d1f6
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220898"
---
# <a name="common-problems-when-creating-a-release-build"></a>リリース ビルド作成時によくある問題

開発中は、通常の構築し、プロジェクトのデバッグ ビルドでテストされます。 リリース ビルド用のアプリケーションをビルドし、アクセス違反が発生する可能性があります。

以下の一覧は、デバッグとリリース (非デバッグ) ビルドの間の主な違いを示しています。 その他の違いがありますが、デバッグ ビルドでうまく機能するとき、リリース ビルドで、アプリケーションにエラーが発生する主な違いを次に示します。

- [ヒープ レイアウト](#_core_heap_layout)

- [コンパイル](#_core_compilation)

- [ポインターのサポート](#_core_pointer_support)

- [最適化](#_core_optimizations)

参照してください、 [/GZ (キャッチ リリース ビルド エラーのデバッグ ビルドで)](reference/gz-enable-stack-frame-run-time-error-checking.md)リリースをキャッチする方法については、コンパイラ オプションはデバッグ ビルドでエラーをビルドします。

##  <a name="_core_heap_layout"></a> ヒープ レイアウト

ヒープ レイアウトは、デバッグがないリリースで動作するアプリケーションの約 90% を明らかな問題の原因になります。

デバッグするためにプロジェクトをビルドすると、デバッグ メモリ アロケーターを使用しています。 これは、すべてのメモリ割り当ての周囲に配置するガード バイトであることを意味します。 これらガード バイトがメモリの上書きを検出します。 ヒープ レイアウトはリリースおよびデバッグの間で異なるため、バージョンでは、メモリの上書きは、デバッグ ビルドで問題を作成しない可能性がありますが、リリース ビルドで致命的な影響があります。

詳細については、次を参照してください。[メモリ上書きのチェック](checking-for-memory-overwrites.md)と[、デバッグ ビルドにチェックを使用して、メモリ上書きの](using-the-debug-build-to-check-for-memory-overwrite.md)します。

##  <a name="_core_compilation"></a> コンパイル

MFC マクロとリリースをビルドするときは、MFC 実装の変更の多くの多くは。 具体的には、ASSERT マクロは、アサートで見つかったコードのいずれも実行されるため、リリース ビルドでは nothing に評価されます。 詳細については、次を参照してください。 [ASSERT ステートメントの確認](using-verify-instead-of-assert.md)します。

一部の関数では、リリース ビルドで速度を上げるためインライン化できません。 一般に、最適化は、リリース ビルドでになっています。 さまざまなメモリ アロケーターが使用されてもいます。

##  <a name="_core_pointer_support"></a> ポインターのサポート

デバッグ情報の不足は、アプリケーションからの余白を削除します。 無効なポインターでは、リリース ビルドで情報をデバッグするのではなく、初期化されていないメモリを指す可能性が高くがあります。

##  <a name="_core_optimizations"></a> 最適化

、特定のコード セグメントの性質に応じて最適化コンパイラは、予期しないコードを生成可能性があります。 これはリリース ビルドの問題の最も可能性の高い原因ですが、場合によっては、発生する場合は。 ソリューションで、次を参照してください。[コードの最適化](optimizing-your-code.md)します。

## <a name="see-also"></a>関連項目

[リリース ビルド](release-builds.md)<br/>
[リリース ビルドの問題の解決](fixing-release-build-problems.md)
