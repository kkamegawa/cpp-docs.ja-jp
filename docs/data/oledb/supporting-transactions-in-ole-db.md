---
title: OLE DB でのトランザクションのサポート
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: 3c71200e39641a69443599e0445f89f469aceeda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389269"
---
# <a name="supporting-transactions-in-ole-db"></a>OLE DB でのトランザクションのサポート

A[トランザクション](../../data/transactions-mfc-data-access.md)グループ、またはバッチの場合は、コミットない (場合のいずれかが失敗した) か、または成功すべてが同時にコミットして、一連のデータ ソースを更新する方法は、トランザクション全体がロールバックされます。 このプロセスは、データ ソースの結果の整合性を維持します。

OLE DB では、次の 3 つの方法でトランザクションをサポートしています。

- [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction::Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction::Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>セッションとトランザクションの関係

1 つのデータ ソース オブジェクトは、特定の時点でトランザクションのスコープの内外をそれぞれが 1 つまたは複数のセッション オブジェクトを作成できます。

セッションがトランザクションを入力しない場合にそのセッションで、データ ストアに対して行われたすべての作業がメソッド呼び出しのたびに即座にコミットします。 (これとも呼ば自動コミット モードまたは暗黙的なモードです。)

セッションでは、トランザクションが入ると、そのセッションで、データ ストアに対して行われたすべての作業がトランザクションの一部とがコミットまたは中止単一ユニットとして。 (これとも呼ば手動コミット モードです。)

トランザクションのサポートは、プロバイダー固有です。 プロバイダーを使用しているが、トランザクションをサポートするためのセッション オブジェクトをサポートしているかどうか`ITransaction`と`ITransactionLocal`(ネストされていない) トランザクションを入力できます。 OLE DB テンプレート クラス[CSession](../../data/oledb/csession-class.md) Visual C にトランザクションのサポートを実装することをお勧めの方法であり、これらのインターフェイスをサポートしています。

## <a name="starting-and-ending-the-transaction"></a>最初と最後のトランザクション

呼び出す、 `StartTransaction`、 `Commit`、および`Abort`コンシューマーの行セット オブジェクト内のメソッド。

呼び出す`ITransactionLocal::StartTransaction`新しいローカル トランザクションが開始されます。 トランザクションを開始するときに、トランザクションをコミットするまでデータ ストアに以降の操作で要求されるすべての変更が適用されません。

呼び出す`ITransaction::Commit`または`ITransaction::Abort`トランザクションを終了します。 `Commit` データ ストアに適用するトランザクションのスコープ内のすべての変更を発生します。 `Abort` トランザクションを開始する前に、トランザクションを中止して、データ ストアのスコープ内のすべての変更は、状態のままに、その原因がありました。

## <a name="nested-transactions"></a>入れ子になったトランザクション

A[トランザクションを入れ子になった](/previous-versions/windows/desktop/ms716985(v=vs.85))セッションにアクティブなトランザクションが存在する場合は、新しいローカル トランザクションを開始するときに発生します。 現在のトランザクションの下に入れ子になったトランザクションとしての新しいトランザクションを開始します。 プロバイダーが入れ子になったトランザクションをサポートしていない場合は、呼び出す`StartTransaction`XACT_E_XTIONEXISTS が返されます、セッションにアクティブなトランザクションがあるときにします。

## <a name="distributed-transactions"></a>分散トランザクション

分散トランザクションは分散型のデータを更新するトランザクションです。つまり、1 つ以上のネットワーク コンピューターのシステム データ。 分散システムでトランザクションをサポートする場合は、OLE DB のトランザクション サポートではなく、.NET Framework を使用する必要があります。

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)