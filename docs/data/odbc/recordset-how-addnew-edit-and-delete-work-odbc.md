---
title: "レコードセット: AddNew、Edit、Delete の動作のしくみ (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddNew メソッド"
  - "データ (レコードセットの) [C++]"
  - "ODBC レコードセット [C++], 追加 (レコードを)"
  - "ODBC レコードセット [C++], 削除 (レコードを)"
  - "ODBC レコードセット [C++], 編集 (レコードを)"
  - "レコード編集 [C++], レコードセットで"
  - "レコード [C++], 追加"
  - "レコード [C++], 削除 (レコードセットで)"
  - "レコード [C++], 編集"
  - "レコード [C++], 更新"
  - "レコードセット [C++], 追加 (レコードを)"
  - "レコードセット [C++], 削除 (レコードを)"
  - "レコードセット [C++], 編集 (レコードを)"
  - "レコードセット [C++], 更新"
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# レコードセット: AddNew、Edit、Delete の動作のしくみ (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

このトピックの内容は、MFC ODBC クラスに該当します。  
  
 このトピックでは、`CRecordset` クラスの `AddNew`、**Edit**、および **Delete** の各メンバー関数の動作のしくみについて説明します。  ここでは、次の内容について説明します。  
  
-   [レコード追加のしくみ](#_core_adding_a_record)  
  
-   [追加したレコードの参照可能範囲](#_core_visibility_of_added_records)  
  
-   [レコード編集のしくみ](#_core_editing_an_existing_record)  
  
-   [レコード削除のしくみ](#_core_deleting_a_record)  
  
> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。  バルク行フェッチを使用する場合は、「[レコードセット : バルク行フェッチ \(ODBC\)](../Topic/Recordset:%20Fetching%20Records%20in%20Bulk%20\(ODBC\).md)」を参照してください。  
  
 「[レコード フィールド エクスチェンジ : RFX の動作のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)」も参照してください。更新処理における RFX の役割について説明しています。  
  
##  <a name="_core_adding_a_record"></a> レコードの追加  
 レコードセットに新しいレコードを追加するには、レコードセットのメンバー関数 [AddNew](../Topic/CRecordset::AddNew.md) を呼び出して新しいレコードのフィールド データ メンバー値を設定し、メンバー関数 [Update](../Topic/CRecordset::Update.md) を呼び出してレコードをデータ ソースに書き出します。  
  
 `AddNew` を呼び出すときは、レコードセットを読み取り専用で開かないでください。  レコードセットが更新可能かどうかは、`CanUpdate` メンバー関数および `CanAppend` メンバー関数で調べます。  
  
 `AddNew` を呼び出すと、次の処理が行われます。  
  
-   エディット バッファー内のレコードが待避されます。これにより、操作を取り消したときに内容を復元できます。  
  
-   後で変更が加えられたことを確認できるように、フィールド データ メンバーにフラグが設定されます。  フィールド データ メンバーは、クリーンである \(変更が加えられていない\) ことが示され、値が Null \(データベース上で値がないということを表す記号\) に設定されます。  
  
 `AddNew` を呼び出した後、エディット バッファーは、新しい空のレコードを表しています。  このレコードの値を設定するには、エディット バッファーの各フィールドに値を直接代入します。  具体的なデータ値をフィールドに指定せずに `SetFieldNull` を呼び出すと、Null 値を指定できます。  
  
 変更内容をコミットするには、**Update** を呼び出します。  新しいレコードに対して **Update** を呼び出すと、次の処理が行われます。  
  
-   ODBC API 関数 **::SQLSetPos** をサポートしている ODBC ドライバーを使っている場合、MFC は、この関数を使ってデータ ソースにレコードを追加します。  **::SQLSetPos** 関数を使用すると、MFC は効率的にレコードを追加できます。これは、SQL ステートメントの構築および処理が必要ないためです。  
  
-   **::SQLSetPos** を使えない場合、MFC は以下の処理を行います。  
  
    1.  変更されていない場合、**Update** は、何もせずに 0 を返します。  
  
    2.  変更されている場合、**Update** は、SQL **INSERT** ステートメントを作成します。  値が変更されたフィールド データ メンバーに対応する列が、**INSERT** ステートメントによって指定されます。  特定の列を強制的に **INSERT** ステートメントに取り込むには、メンバー関数 [SetFieldDirty](../Topic/CRecordset::SetFieldDirty.md) を呼び出します。  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Update** では、新しいレコードがコミットされます。つまり、トランザクションの進行中以外は、**INSERT** ステートメントが実行され、新しいレコードがデータ ソース上のテーブル \(およびスナップショットがない場合はレコードセット\) にコミットされます。  
  
    4.  待避されていたレコードがエディット バッファーに復元されます。  **INSERT** ステートメントの成功\/失敗に関係なく、`AddNew` を呼び出す前に現在のレコードであったレコードが再び現在のレコードになります。  
  
    > [!TIP]
    >  新しいレコードを詳細に制御するには、値が必要なすべてのフィールドに値を設定し、値が不要なフィールドには、そのフィールドへのポインターと **TRUE** に設定されたパラメーター \(既定\) で `SetFieldNull` を呼び出して、明示的に Null を設定します。  特定のフィールドをデータ ソースに書き出さないようにするには、フィールドへのポインターとパラメーター **FALSE** で `SetFieldDirty` を呼び出して、フィールドの値を変更しないようにします。  フィールドの値として NULL を設定できるかどうかを調べるには、`IsFieldNullable` を呼び出します。  
  
    > [!TIP]
    >  レコードセット データ メンバーの値の変更を検出するために、MFC では、レコードセットに格納できる各データ型に適切な **PSEUDO\_NULL** 値を使用しています。  既に NULL として印が付けられるフィールドに、明示的に **PSEUDO\_NULL** を設定するには、第 1 パラメーターとしてフィールドのアドレス、第 2 パラメーターとして **FALSE** を指定して、関数 `SetFieldNull` を呼び出します。  
  
##  <a name="_core_visibility_of_added_records"></a> 追加したレコードの参照可能範囲  
 レコードセットに追加したレコードは、すぐに使えるようになるとは限りません。  レコードの参照可能範囲は、以下の 2 つの条件によって左右されます。  
  
-   ドライバーのサポート範囲  
  
-   フレームワークが活用できるドライバーの機能  
  
 ODBC API 関数 **::SQLSetPos** をサポートする ODBC ドライバーを使っている場合、MFC はこの関数を使ってレコードを追加します。  関数 **::SQLSetPos** を使った場合は、追加したレコードは、更新可能なすべての MFC レコードセットからアクセスできるようになります。  この関数をサポートしていない場合は、追加されたレコードを参照できません。追加されたレコードを参照するには、**Requery** を呼び出す必要があります。  また、**::SQLSetPos** を使った場合の方がより効率的です。  
  
##  <a name="_core_editing_an_existing_record"></a> 既存のレコードの編集  
 レコードセット内の既存のレコードを編集するには、目的のレコードにスクロールし、メンバー関数 [Edit](../Topic/CRecordset::Edit.md) を呼び出します。次に、新しいレコードのフィールド データ メンバーの値を設定し、メンバー関数 [Update](../Topic/CRecordset::Update.md) を呼び出してレコードをデータ ソースに書き出します。  
  
 **Edit** を呼び出すときは、レコードセットを更新可能にし、編集するレコードに移動しておきます。  レコードセットが更新可能かどうかは、`CanUpdate` メンバー関数および `IsDeleted` メンバー関数で調べます。  また、現在のレコードが削除されておらず、レコードセット内にレコードが存在している必要があります \(`IsBOF` と `IsEOF` の両方が 0 を返す必要があります\)。  
  
 **Edit** を呼び出すと、エディット バッファー内のレコード \(現在のレコード\) が待避されます。  待避されたレコードは、各フィールドが変更されたかどうかを確認するために後で使います。  
  
 **Edit** を呼び出すと、エディット バッファーは現在のレコードを指したままですが、フィールド データ メンバーを変更できるようになります。  レコードを変更するには、フィールド データ メンバーの値を直接変更します。  具体的なデータ値をフィールドに指定せずに `SetFieldNull` を呼び出すと、Null 値を指定できます。  変更をコミットするには、**Update** を呼び出します。  
  
> [!TIP]
>  `AddNew` モードまたは **Edit** モードを終了するには、**AFX\_MOVE\_REFRESH** パラメーターを指定して **Move** を呼び出します。  
  
 **Update** を呼び出すときは、レコードセットが空でなく、現在のレコードが削除されていないことが必要です。  つまり、`IsBOF`、`IsEOF`、および `IsDeleted` がすべて 0 を返す必要があります。  
  
 編集されたレコードに対して **Update** を呼び出すと、次の処理が行われます。  
  
-   ODBC API 関数 **::SQLSetPos** をサポートしている ODBC ドライバーを使っている場合、MFC は、この関数を使ってデータ ソースのレコードを変更します。  関数 **::SQLSetPos** を使って、ドライバーは対応するサーバー上のレコードとエディット バッファーを比較し、変更されている場合はサーバー上のレコードを変更します。  **::SQLSetPos** 関数を使用すると、MFC は効率的にレコードを更新できます。これは、SQL ステートメントの構築および処理が必要ないためです。  
  
     または  
  
-   **::SQLSetPos** を使えない場合、MFC は以下の処理を行います。  
  
    1.  変更されていない場合、Update は、何もせずに 0 を返します。  
  
    2.  変更されている場合、**Update** は、SQL **UPDATE** ステートメントを作成します。  値が変更されたフィールド データ メンバーに対応する列が、**UPDATE** ステートメントによって指定されます。  
  
    3.  **Update** が変更をコミットします。つまり、**UPDATE** ステートメントが実行され、データ ソース上のレコードが変更されます。ただし、トランザクションが進行中の場合はコミットされません。トランザクションが更新に与える影響については、「[トランザクション : レコードセットからのトランザクション実行 \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」を参照してください。  ODBC が保持するレコードのコピーも更新されます。  
  
    4.  `AddNew` の場合とは異なり、**Edit** の処理では、待避したレコードは復元されません。  編集後のレコードが現在のレコードになります。  
  
    > [!CAUTION]
    >  **Update** を呼び出してレコードセットを更新する前に、テーブルの主キーを構成するすべての列 \(または、テーブル上の一意なインデックスを構成するすべての列か、行を一意に識別するのに十分な数の列\) がレコードセットに含まれていることに注意してください。  場合によっては、フレームワークは、レコードセット内で選択されている列だけに基づいてテーブル内の更新するレコードを特定します。  選択されている列数が不足していると、テーブル内の複数のレコードが更新されてしまう場合があります。  この場合は、**Update** を呼び出した結果として例外がスローされます。  
  
    > [!TIP]
    >  `AddNew` または **Edit** のいずれかを呼び出した後、**Update** を呼び出さずに、再びいずれかの関数を呼び出すと、エディット バッファーが再表示され、待避しておいたレコードの値に戻ります。  つまり、`AddNew` または **Edit** を中止してやり直すことができます。編集中のレコードが間違っていることに気付いたときは、再び `AddNew` または **Edit** を呼び出してやり直せます。  
  
##  <a name="_core_deleting_a_record"></a> レコードの削除  
 レコードセットのレコードを削除するには、目的のレコードにスクロールし、レコードセットのメンバー関数 [Delete](../Topic/CRecordset::Delete.md) を呼び出します。  `AddNew` および **Edit** の場合とは異なり、**Delete** の後は **Update** を呼び出す必要がありません。  
  
 **Delete** を呼び出すときは、レコードセットを更新可能にし、削除するレコードに移動しておきます。  メンバー関数 `CanUpdate`、`IsBOF`、`IsEOF`、および `IsDeleted` によってこれらの状態をチェックできます。  
  
 **Delete** を呼び出すと、次の処理が行われます。  
  
-   ODBC API 関数 **::SQLSetPos** をサポートしている ODBC ドライバーを使っている場合、MFC は、この関数を使ってデータ ソースのレコードを削除します。  関数 **::SQLSetPos** を使うと、MFC が効率的にレコードを削除できます。これは、SQL ステートメントの構築、実行が必要ないためです。  
  
     または  
  
-   **::SQLSetPos** を使えない場合、MFC は以下の処理を行います。  
  
    1.  `AddNew` および **Edit** の場合と同様に、エディット バッファー内の現在のレコードはバックアップされません。  
  
    2.  **Delete** では、レコードを削除する SQL **DELETE** ステートメントを作成します。  
  
         `AddNew` および **Edit** の場合とは異なり、エディット バッファーの現在のレコードは格納されません。  
  
    3.  **DELETE** ステートメントが実行されます。  データ ソース上のレコードに、削除されたことを示す印が付けられます。また、レコードセットがスナップショットの場合は、ODBC 上のレコードにも削除の印が付けられます。  
  
    4.  削除されたレコードの値はレコードセットのフィールド データ メンバー上に残っていますが、フィールド データ メンバーには Null であることを表す印が付けられています。したがって、レコードセットの `IsDeleted` メンバー関数は 0 以外の値を返します。  
  
    > [!NOTE]
    >  レコードを削除したら、別のレコードにスクロールして、エディット バッファーの値を新しいレコードの値にする必要があります。  **Delete** を再度呼び出すか、**Edit** を呼び出すと、エラーが発生します。  
  
 更新処理で使用する SQL ステートメントについては、「[SQL](../../data/odbc/sql.md)」を参照してください。  
  
## 参照  
 [レコードセット \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [レコードセット: 更新処理の詳細 \(ODBC\)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [レコード フィールド エクスチェンジ \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)