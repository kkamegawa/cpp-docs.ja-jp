---
title: 読み取り専用プロバイダーのテスト
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: a9601b2afe40133a5cc88589b530b5ed549ac81e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389230"
---
# <a name="testing-the-read-only-provider"></a>読み取り専用プロバイダーのテスト

プロバイダーをテストするには、コンシューマーが必要です。 コンシューマーがプロバイダーと一致できる場合に役立ちます。 OLE DB コンシューマー テンプレートは、OLE DB の thin ラッパーでプロバイダーの COM オブジェクトと一致します。 ソースは、コンシューマー テンプレートに含まれる、ために、それらのプロバイダーのデバッグが容易になります。 コンシューマー テンプレートも非常に小さく、高速のコンシューマー アプリケーションを開発する方法。

このトピックの例では、テストのコンシューマーの MFC アプリケーション ウィザードの既定のアプリケーションを作成します。 テスト アプリケーションは、OLE DB コンシューマー テンプレート コードが追加された単純なダイアログです。

## <a name="to-create-the-test-application"></a>テスト アプリケーションを作成するには

1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

1. **プロジェクトの種類**ペインで、**インストール済み** > **Visual C** > **MFC/ATL**フォルダー。 **テンプレート**ペインで、 **MFC アプリケーション**します。

1. プロジェクト名を入力*TestProv*、順にクリックします**OK**します。

   **MFC アプリケーション**ウィザードが表示されます。

1. **アプリケーションの種類**] ページで、[**ダイアログ ベース**します。

1. **高度な機能**] ページで、[ **Automation**、順にクリックします**完了**します。

> [!NOTE]
> 追加する場合に、アプリケーションでオートメーションのサポートが必要ありません`CoInitialize`で`CTestProvApp::InitInstance`します。

表示および編集することができます、 **TestProv**で選択 ダイアログ ボックス (IDD_TESTPROV_DIALOG)**リソース ビュー**します。 ダイアログ ボックスで、行セット内の各文字列に 1 つずつ、2 つのリスト ボックスを配置します。 並べ替えプロパティのキーを押して両方のリスト ボックスをオフにする**Alt**+**」と入力**リスト ボックスがオンの場合、設定、**並べ替え**プロパティを**False**します。 また、配置、**実行**ファイルをフェッチするダイアログ ボックスのボタン。 完成した**TestProv**  ダイアログ ボックスが「文字列 1」と"2 を String"をそれぞれという 2 つのリスト ボックスにある必要があります以外もあります**OK**、**キャンセル**、および**実行。** ボタン。

(このケース TestProvDlg.h) で、ダイアログ クラスのヘッダー ファイルを開きます。 (、クラス宣言の外部のヘッダー ファイルに次のコードを追加します。

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

class CProvider
{
// Attributes
public:
   char   szField1[16];
   char   szField2[16];

   // Binding Maps
BEGIN_COLUMN_MAP(CProvider)
   COLUMN_ENTRY(1, szField1)
   COLUMN_ENTRY(2, szField2)
END_COLUMN_MAP()
};
```

コードでは、行セット内になります列を定義するユーザー レコードを表します。 クライアントを呼び出すと`IAccessor::CreateAccessor`、これらのエントリを使用してバインドする列を指定します。 OLE DB コンシューマー テンプレートでは、列を動的にバインドすることもできます。 COLUMN_ENTRY マクロは、PROVIDER_COLUMN_ENTRY マクロのクライアント側バージョンです。 2 つの COLUMN_ENTRY マクロでは、序数、2 つの文字列型、長さ、およびデータ メンバーを指定します。

ハンドラー関数を追加、**実行**ボタンを押して**Ctrl**  をダブルクリックして、**実行**ボタンをクリックします。 関数では、次のコードを配置します。

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
      return;

   while (table.MoveNext() == S_OK)
   {
      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
   }
}
```

`CCommand`、 `CDataSource`、および`CSession`OLE DB コンシューマー テンプレートに属しているすべてのクラス。 各クラスは、プロバイダーでの COM オブジェクトを模倣します。 `CCommand`オブジェクトは、`CProvider`クラス、テンプレート パラメーターとして、ヘッダー ファイルで宣言します。 `CProvider`パラメーターは、プロバイダーからデータにアクセスするために使用するバインドを表します。 

各クラスを開く行では、プロバイダーの各 COM オブジェクトを作成します。 プロバイダを探しを使用して、`ProgID`のプロバイダー。 取得することができます、`ProgID`システム レジストリからや Custom.rgs ファイル内の検索 (プロバイダーのディレクトリを開き、検索、`ProgID`キー)。

MyData.txt ファイルに含まれている、`MyProv`サンプル。 エディターの使用、独自のファイルを作成し、偶数のキーを押して文字列を入力する**Enter**各文字列の間。 ファイルを移動する場合は、パス名を変更します。

文字列を渡す"c:\\\samples\\\myprov\\\MyData.txt"で、`table.Open`行。 ステップ インする場合、`Open`にこの文字列が渡されることを確認する呼び出し、`SetCommandText`プロバイダーのメソッド。 なお、`ICommandText::Execute`メソッドは、その文字列を使用します。

データをフェッチする呼び出す`MoveNext`テーブルにします。 `MoveNext` 呼び出し、 `IRowset::GetNextRows`、 `GetRowCount`、および`GetData`関数。 これ以上の行がある場合 (つまり、行セット内の現在位置がより大きい`GetRowCount`)、ループを終了します。

これ以上の行が存在する場合、プロバイダーは、DB_S_ENDOFROWSET を返します。 DB_S_ENDOFROWSET 値は、エラーではありません。 データのフェッチのループをキャンセルし、SUCCEEDED マクロを使用しない S_OK に対して常に確認する必要があります。

ビルドし、プログラムをテストできるようになりましたにします。

## <a name="see-also"></a>関連項目

[単純な読み取り専用プロバイダーの機能の拡張](../../data/oledb/enhancing-the-simple-read-only-provider.md)