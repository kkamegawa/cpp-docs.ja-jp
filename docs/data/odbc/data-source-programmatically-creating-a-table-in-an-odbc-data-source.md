---
title: プログラムで、ODBC データ ソースにテーブルを作成します。
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 61d3f3e39362db27d1e3abc00fa3cb9ea82b86e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395933"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>データ ソース:データ ソース : プログラムにおける ODBC データ ソースのテーブルの作成

このトピックでは、データのテーブルを作成する方法を説明しますを使用して、ソース、`ExecuteSQL`クラスのメンバー関数`CDatabase`、関数を含む文字列を渡して、 **CREATE TABLE** SQL ステートメント。

MFC での ODBC データ ソースの詳細については、次を参照してください。[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)します。 トピック[データ ソース。ODBC データ ソースをプログラムで構成](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)データ ソースの作成について説明します。

確立されているデータ ソースの場合を使用してテーブルを簡単に作成することができます、`ExecuteSQL`メンバー関数および**CREATE TABLE** SQL ステートメント。 ある場合など、`CDatabase`と呼ばれるオブジェクト`myDB`テーブルを作成する次の MFC コードを使用できます。

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

このコード例は、によって管理される Microsoft Access データ ソース接続で「オフィス」をという名前のテーブルを作成します。 `myDB`; テーブルには、2 つのフィールド"OfficeID"と"OfficeName。"が含まれています。

> [!NOTE]
>  指定されたフィールドの種類、 **CREATE TABLE** SQL ステートメントが使用している ODBC ドライバーによって異なる場合があります。 (C++ 1.5 で視覚的に分散) の Microsoft Query プログラムは、データ ソースに使用できるフィールドの型を検出する方法の 1 つです。 Microsoft のクエリで次のようにクリックします。**ファイル**、 をクリック**Table_Definition**、データ ソースからテーブルを選択し、に表示される種類を見て、**型**コンボ ボックス。 SQL 構文は、インデックスの作成にも存在します。

## <a name="see-also"></a>関連項目

[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)