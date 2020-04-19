---
title: TN026:DDX ルーチンおよび DDV ルーチン
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 89916e60d9677240f2d70e37e9a80e6ad7a76fc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305867"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026:DDX ルーチンおよび DDV ルーチン

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

ここでは、ダイアログ データ エクス (チェンジ DDX) とダイアログ データ検証 (DDV) のアーキテクチャについて説明します。 また、DDX_ または DDV_ プロシージャを作成する方法と、ルーチンを使用する ClassWizard を拡張する方法についても説明します。

## <a name="overview-of-dialog-data-exchange"></a>ダイアログ データ エクス チェンジの概要

すべてのダイアログ データ関数は、C++ コードで実行されます。 マクロや特別なリソースはありません。 メカニズムの心臓部は、仮想関数ダイアログ データの交換をすべてのダイアログ クラスでオーバーライドされると検証。 このフォームは常にあります。

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

特殊な形式の AFX コメントは、ClassWizard を見つけ、この関数内のコードの編集を許可します。 ClassWizard と互換性がないコードは、特殊な形式のコメントの外側に配置する必要があります。

上記の例では、 \<data_exchange_function_call > 形式では。

```cpp
DDX_Custom(pDX, nIDC, field);
```

\<data_validation_function_call > は省略可能で、フォームで。

```cpp
DDV_Custom(pDX, field, ...);
```

各 DDX_/ddv の 1 つ以上のペアを含めることができない`DoDataExchange`関数。

すべてのダイアログ データ エクス チェンジ ルーチンと MFC で提供されるダイアログ データ検証ルーチンの一覧については、'afxdd_.h' を参照してください。

ダイアログ データはその: でのメンバー データ、`CMyDialog`クラス。 構造体または同様のものでは保存されません。

## <a name="notes"></a>メモ

すべての機能はから派生したクラスで使用できますが、この「ダイアログ データ」と呼ば`CWnd`だけのダイアログ ボックスに限定されないとします。

データの初期値は、標準 C++ コンス トラクター ブロックでは、通常で設定`//{{AFX_DATA_INIT`と`//}}AFX_DATA_INIT`コメント。

`CWnd::UpdateData` 初期化とエラーの呼び出しを処理を行う操作は、`DoDataExchange`します。

呼び出すことができます`CWnd::UpdateData`データ交換および検証を実行するには、いつでもできます。 既定で`UpdateData`(TRUE) は、既定で呼び出されます`CDialog::OnOK`ハンドラーと`UpdateData`(FALSE) が既定値で呼び出される`CDialog::OnInitDialog`します。

そのため、DDX_ ルーチンの直後にする必要があります DDV_ ルーチン*フィールド*します。

## <a name="how-does-it-work"></a>しくみ

ダイアログ データを使用するには、次を理解する必要はありません。 ただし、バック グラウンドでこの動作を理解、独自の exchange または検証プロシージャを作成します。

`DoDataExchange`メンバー関数は、非常によく似た、`Serialize`メンバー関数には取得または設定するデータと外部のフォームから責任を負います (ここではダイアログ ボックスで制御) クラスのメンバーのデータとの間。 *PDX*パラメーターのデータ交換を行うためのコンテキストと似ています、`CArchive`パラメーター`CObject::Serialize`します。 *PDX* (、`CDataExchange`オブジェクト)、方向フラグと似ていますが`CArchive`方向フラグがあります。

- 場合`!m_bSaveAndValidate`コントロールにデータの状態を読み込みます。

- 場合`m_bSaveAndValidate`、コントロールからデータの状態を設定します。

検証にのみ発生時に`m_bSaveAndValidate`設定されています。 値`m_bSaveAndValidate`にブール型パラメーターによって決まりますが`CWnd::UpdateData`します。

その他の 3 つの興味深いがある`CDataExchange`メンバー。

- `m_pDlgWnd`:コントロールを格納するウィンドウ (通常はダイアログ) です。 これは、すべて DDX/DDV ルーチンに DDX_ と DDV_ のグローバル関数の呼び出し元が 'this' を渡さずにすることを防ぐためには。

- `PrepareCtrl`、および`PrepareEditCtrl`:データ交換用のダイアログ コントロールを準備します。 検証が失敗した場合、フォーカスを設定するため、そのコントロールのハンドルを格納します。 `PrepareCtrl` 非編集コントロールの使用と`PrepareEditCtrl`編集コントロールが使用されます。

- `Fail`:ユーザーが入力エラーを警告メッセージ ボックスの後に呼び出されます。 このルーチンは、最後のコントロールにフォーカスを復元 (最後の呼び出し`PrepareCtrl`または`PrepareEditCtrl`)、例外をスローします。 このメンバー関数は、DDX_ と DDV_ ルーチンから呼び出すことができます。

## <a name="user-extensions"></a>ユーザーの拡張機能

既定の DDX/DDV メカニズムを拡張するいくつかの方法はあります。 次の操作を行うことができます。

- 新しいデータ型を追加します。

    ```cpp
    CTime
    ```

- 新しい exchange プロシージャ (DDX_) を追加します。

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- 新しい検証プロシージャ (DDV_) を追加します。

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- 任意の式を検証プロシージャに渡します。

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > このような任意の式は ClassWizard で編集することはできず、特殊な形式のコメントの外部で移動する必要があります (//{{AFX_DATA_MAP(CMyClass)) します。

`DoDialogExchange`メンバー関数には、条件文または混合の交換と検証の関数呼び出しで、その他の有効な C++ ステートメントが含まれます。

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> 上記のように、このようなコードは ClassWizard で編集することはできませんし、特殊な形式のコメントの外側でのみ使用する必要があります。

## <a name="classwizard-support"></a>ClassWizard サポート

ClassWizard では、ClassWizard のユーザー インターフェイスに、独自の DDX_ と DDV_ ルーチンを統合することを許可することで DDX/DDV カスタマイズのサブセットをサポートしています。 費用効果は、特定 DDX ルーチンおよび DDV ルーチンまたは多くのプロジェクトでプロジェクトを再利用する予定の場合、これを行います。

これを行うには、特殊なエントリは、DDX で行われます。CLW (以前のバージョンの Visual C は、APSTUDIO にこの情報を格納します。INI) またはプロジェクトの。CLW ファイルです。 特殊なエントリは、プロジェクトの [一般情報] セクションでいずれかを入力します。CLW ファイルまたは、DDX の [ExtraDDX] セクション。\Program Files\Microsoft Visual Studio\Visual CLW ファイルC++\bin ディレクトリ。 DDX を作成する必要があります。存在しない場合は、ファイルを CLW です。 特定のプロジェクトでのみカスタム DDX_/ddv ルーチンを使用する場合は、プロジェクトの [一般情報] セクションにエントリを追加します。CLW ファイルを代わりにします。 多くのプロジェクトで、ルーチンを使用する場合は、DDX の [ExtraDDX] セクションにエントリを追加します。CLW します。

これらの特殊なエントリの一般的な形式です。

> ExtraDDXCount=*n*

場所*n* ExtraDDX の数ですかには、フォームの行。

> ExtraDDX?=*keys*; *vb-keys*; *prompt*; *type*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

どこ。 数値 1 - *n* DDX 型で定義されている一覧を示します。

各フィールドは、';' 文字で区切られます。 フィールドとその目的を次に示します。

- *keys*

  この変数の型を許可するダイアログ コントロールを示す 1 つの文字の一覧。

  |文字|許可されているコントロール|
  |-|-|
  E | 編集
  C | 2 つの状態のチェック ボックス
  c | 3 つの状態のチェック ボックス
  R | グループ内の最初のラジオ ボタン
  L | に比べてリスト ボックス
  l | 並べ替えられたリスト ボックス
  M | (アイテムの編集) を含むコンボ ボックス
  N | に比べてボックスの一覧
  n | 並べ替えられたボックスの一覧
  1 | DDX 挿入リストの先頭に追加する必要があります (既定値は末尾に追加) これは、通常使用の DDX ルーチン 'コントロール' プロパティを転送します。

- *vb-keys*

  このフィールドは、(VBX コントロールは、32 ビットの製品ではサポートされません) VBX コントロールの 16 ビットの製品でのみ使用されます。

- *prompt*

  プロパティ コンボ ボックス (引用符なし) に指定する文字列

- *type*

  ヘッダー ファイルに出力する型の単一の識別子。 DDX_Time で上記の例では、これは CTime に設定が。

- *vb-keys*

  このバージョンでは使用されず、空は常に

- *initValue*

  初期値-0 または空です。 空白の場合は、初期化行が、実装ファイルの//{{AFX_DATA_INIT セクションでは書き込まれません。 空のエントリは、C++ オブジェクトのために使用する必要があります (など`CString`、`CTime`など) が適切な初期化を保証するコンス トラクターがあります。

- *DDX_Proc*

  DDX_ プロシージャの 1 つの識別子。 C++関数名は"DDX"で開始する必要がありますに"このを含めないでください、 \<DDX_Proc > 識別子。 上記の例では、 \<DDX_Proc > 識別子は時間になります。 ClassWizard の関数呼び出しで、実装ファイルを書き込む場合、{{AFX_DATA_MAP セクションでは、この名前に追加 DDX DDX_Time に到着するためです。

- *comment*

  ダイアログ ボックスのこの DDX の変数を表示するコメントです。 ここであり、通常の機能が提供する DDX/DDV ペアによって実行される操作について説明するテキストを配置します。

- *DDV_Proc*

  エントリの DDV 部分は省略可能です。 すべての DDX ルーチンでは、対応する DDV ルーチンがあります。 多くの場合、転送の不可欠な部分として検証フェーズを含める方が便利です。 これは多くの場合、場合 DDV ルーチンは、すべてのパラメーターを必要としない ClassWizard では、パラメーターなしの DDV ルーチンをサポートしていないためです。

- *arg*

  DDV_ プロシージャの 1 つの識別子。 C++関数名は"DDV_"で開始する必要がありますが、"このに含めないでください、 \<DDX_Proc > 識別子。

  *arg* DDV 引数を 1 つまたは 2 が続きます。

   - *promptN*

      アイテム編集 (& accelerator) の上に配置する文字列。

   - *fmtN*

      1 つの引数型の書式指定文字:

      |文字|型|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | int を長時間かかる場合 (つまり、時間の長い)|
      |U | 符号なし長 (つまり、DWORD)|
      |f | フローティング|
      |F | 二重線|
      |s | string|

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
