---
title: EDITBIN オプション
description: Microsoft EDITBIN ユーティリティのコマンドラインオプションのリファレンスガイドです。
ms.date: 02/09/2020
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: c27172522ceabeccd06d7b957aa791edc49beec8
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257703"
---
# <a name="editbin-options"></a>EDITBIN オプション

EDITBIN を使用して、オブジェクトファイル、実行可能ファイル、およびダイナミックリンクライブラリ (Dll) を変更できます。 オプションは、EDITBIN によって行われる変更を指定します。

オプションは、ダッシュ (`-`) またはスラッシュ (`/`) のいずれかのオプション指定子で構成され、その後にオプションの名前が続きます。 オプション名を省略することはできません。 一部のオプションでは、コロン (`:`) の後に指定された引数を受け取ります。 1 つのオプションの指定には、スペースやタブは挿入できません。 複数のオプションを指定する場合は、各オプションを 1 つ以上のスペースまたはタブで区切ります。 オプション名とそのキーワード引数またはファイル名引数では、大文字と小文字が区別されません。 たとえば、`-bind` と `/BIND` は同じことを意味します。

EDITBIN には次のオプションがあります。

|オプション|目的|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|DLL をバインドできるかどうかを指定します。|
|[/ALLOWISOLATION](allowisolation.md)|DLL または実行可能ファイルマニフェストの参照動作を指定します。|
|[/APPCONTAINER](appcontainer.md)|アプリが、UWP アプリなど、AppContainer 内で実行される必要があるかどうかを指定します。|
|[/BIND](bind.md)|指定されたオブジェクト内のエントリポイントのアドレスを設定して、読み込み時間を短縮します。|
|[/DYNAMICBASE](dynamicbase.md)|アドレス空間レイアウトのランダム化 (ASLR) を使用して、読み込み時に DLL または実行可能イメージをランダムに再配置できるかどうかを指定します。|
|[/ERRORREPORT](errorreport-editbin-exe.md)| 非推奨。 エラー報告は、 [Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。 |
|[/HEAP](heap.md)|実行可能イメージのヒープのサイズをバイト単位で設定します。|
|[/HIGHENTROPYVA](highentropyva.md)|DLL または実行可能イメージが高いエントロピ (64 ビット) アドレス空間レイアウトのランダム化 (ASLR) をサポートするかどうかを指定します。|
|[/INTEGRITYCHECK](integritycheck.md)|読み込み時にデジタル署名を確認するかどうかを指定します。|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|オブジェクトが 2 gb を超えるアドレスをサポートするかどうかを指定します。|
|[/NOLOGO](nologo-editbin.md)|EDITBIN スタートアップバナーを表示しません。|
|[/NXCOMPAT](nxcompat.md)|実行可能イメージが Windows データ実行防止と互換性があるかどうかを指定します。|
|[/REBASE](rebase.md)|指定されたオブジェクトのベースアドレスを設定します。|
|[/RELEASE](release.md)|ヘッダーにチェックサムを設定します。|
|[/SECTION](section-editbin.md)|セクションの属性をオーバーライドします。|
|[/STACK](stack.md)|実行可能イメージのスタックのサイズをバイト単位で設定します。|
|[/SUBSYSTEM](subsystem.md)|実行環境を指定します。|
|[/SWAPRUN](swaprun.md)|実行可能イメージをスワップファイルにコピーしてから、そこから実行することを指定します。|
|[/TSAWARE](tsaware.md)|アプリがマルチユーザー環境で動作するように設計されていることを指定します。|
|[/VERSION](version.md)|ヘッダーのバージョン番号を設定します。|

## <a name="see-also"></a>参照

[その他の MSVC ビルドツール](c-cpp-build-tools.md)\
[EDITBIN リファレンス](editbin-reference.md)
