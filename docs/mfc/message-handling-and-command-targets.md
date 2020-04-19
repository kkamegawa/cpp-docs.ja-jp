---
title: メッセージ処理とコマンド ターゲット
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: 702cb96da13d6109c17a28e58c08a30af3f77fd4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383803"
---
# <a name="message-handling-and-command-targets"></a>メッセージ処理とコマンド ターゲット

コマンドのディスパッチ インターフェイス`IOleCommandTarget`シンプルかつ拡張可能なクエリを実行し、コマンドを実行するメカニズムを定義します。 このメカニズムは、オートメーションのより単純な`IDispatch`コマンドの標準セットを完全に依存するためのコマンドの引数を持つことはほとんどなく、型情報は必要ありません (タイプ セーフはコマンドの引数も低下)。

コマンドのディスパッチ インターフェイスの設計では、各コマンドがで識別される自体「コマンド グループ」に属している、 **GUID**します。 そのため、新しいグループを定義し、Microsoft との協力する必要や、他のベンダーには、そのグループ内のすべてのコマンドを定義するすべてのユーザーできます。 (これは、同じ手段として定義の本質的には、 **dispinterface** plus **Dispid** Automation でします。 オーバー ラップがあるここでは、このコマンドのルーティング メカニズムはコマンドのルーティングにのみ、大規模なスケールでのスクリプト/プログラミングではなく Automation ハンドルとしてです。)

`IOleCommandTarget` 次のシナリオを処理します。

- インプレース アクティブ化されるだけでは、通常、オブジェクトのツールバーを表示し、オブジェクトのツールバーでは、いくつかのように、コンテナーのコマンドのボタンがありますが、オブジェクトの場合**印刷**、**印刷プレビュー**、 **保存**、**新規**、**ズーム**、およびその他。 (オブジェクトを削除する、インプレース アクティベーション標準をお勧めしますから、ツールバー、またはこのようなボタンは、少なくとも無効にします。 この設計により、これらのコマンドを有効にし、まだ適切なハンドラーにルーティングされます。)現時点では、オブジェクトがコンテナーにこれらのコマンドをディスパッチするメカニズムはありません。

- コンテナーは、コマンドを送信するこのような必要があります (Office バインダー) などの active ドキュメント コンテナーでは、アクティブ ドキュメントが埋め込まれているときに**印刷**、**ページ セットアップ**、**プロパティ**、およびその他のユーザーが含まれているアクティブなドキュメントです。

既存の Automation 標準を通じてこの単純なコマンドのルーティングを処理でき、`IDispatch`します。 ただし、オーバーヘッドが伴う`IDispatch`ここでは、必要なより多くなっていますので`IOleCommandTarget`同じ結果を実現するために簡単な手段を提供します。

```
interface IOleCommandTarget : IUnknown
    {
    HRESULT QueryStatus(
        [in] GUID *pguidCmdGroup,
        [in] ULONG cCmds,
        [in,out][size_is(cCmds)] OLECMD *prgCmds,
        [in,out] OLECMDTEXT *pCmdText);
    HRESULT Exec(
        [in] GUID *pguidCmdGroup,
        [in] DWORD nCmdID,
        [in] DWORD nCmdExecOpt,
        [in] VARIANTARG *pvaIn,
        [in,out] VARIANTARG *pvaOut);
    }
```

`QueryStatus`メソッドをここでは、特定の一連のコマンド セットがで識別されているかどうかをテスト、 **GUID**はサポートされています。 この呼び出しは、配列を格納**OLECMD**コマンドや状態情報の名前を記述するテキストを返すだけでなくコマンドのサポートされている一連の値 (構造体)。 コマンドを渡すことができます、呼び出し元がコマンドを呼び出す必要がある、ときに (とセット**GUID**) に`Exec`戻り値の戻すオプションと引数と。

## <a name="see-also"></a>関連項目

[Active ドキュメント コンテナー](../mfc/active-document-containers.md)
