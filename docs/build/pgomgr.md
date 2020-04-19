---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295254"
---
# <a name="pgomgr"></a>pgomgr

.Pgd ファイルには、1 つまたは複数の .pgc ファイルからプロファイル データを追加します。

## <a name="syntax"></a>構文

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>パラメーター

*options*<br/>
次のオプションを指定できます**pgomgr**:

- **/help**または **/でしょうか。** 使用可能な表示**pgomgr**オプション。

- **/clear** .pgd ファイルすべてのプロファイル情報をクリアします。 .Pgc を指定することはできませんファイル **/clear**を指定します。

- **/detail**フロー グラフのカバレッジ情報を含む、詳細な統計情報が表示されます。

- **/summary**表示関数ごとの統計情報。

- **一意/** を使用すると **/summary**原因の装飾関数名を表示します。 既定値、**一意/** が使用されない場合は非装飾関数名が表示されます。

- **/merge**\[**:**<em>n</em>] は、.pgc ファイルまたは .pgd ファイルに追加するファイルのデータ。 省略可能なパラメーター、 *n*、データを追加する必要がありますを指定する*n*時間。 たとえば、シナリオにどのくらいの頻度は、その顧客を反映するように元に戻すの 6 倍なるよく場合、テストの実行で 1 回実行してで 6 回 .pgd ファイルに追加**した後**します。

*pgcfiles*<br/>
1 つまたは複数の .pgc ファイルのプロファイル データ .pgd ファイルにマージします。 1 つ .pgc ファイルまたは複数の .pgc ファイルを指定できます。 .Pgc ファイルを指定しない場合**pgomgr** .pgd ファイルと同じファイル名を持つが、すべての .pgc ファイルをマージします。

*pgdfile*<br/>
.Pgc ファイルまたはファイルからデータをマージ先 .pgd ファイル。

## <a name="remarks"></a>Remarks

> [!NOTE]
> このツールは、Visual Studio 開発者コマンド プロンプトからのみ起動できます。 システム コマンド プロンプトやエクスプローラーからは開始できません。

## <a name="example"></a>例

この例のコマンドは、プロファイル データの myapp.pgd ファイルをクリアします。

`pgomgr /clear myapp.pgd`

この例のコマンドのプロファイルにデータが追加 myapp1.pgc .pgd ファイルを 3 回。

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

この例では、すべての myapp!#.pgc ファイルからのプロファイル データは myapp.pgd ファイルに追加されます。

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>関連項目

[ガイド付き最適化のプロファイル](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
