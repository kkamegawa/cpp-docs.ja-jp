---
title: "OLE のダイアログ ボックス | Microsoft Docs"
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
  - "ダイアログ ボックス"
  - "ダイアログ ボックス, ダイアログ ボックスの概要"
  - "ダイアログ ボックス, OLE"
  - "挿入 (オブジェクトを)"
  - "MFC ダイアログ ボックス, OLE ダイアログ ボックス"
  - "OLE ダイアログ ボックス"
  - "OLE ダイアログ ボックス, OLE ダイアログ ボックスの概要"
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE のダイアログ ボックス
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ユーザーが OLE 対応アプリケーションを実行しているときに、アクションを実行するためのアプリケーションは、ユーザーの情報が必要な場合があります。  MFC の OLE クラスは、必要な情報を収集するための、いくつかのダイアログ ボックスを表示します。  ここでは、これらのダイアログ ボックスを表示するために必要な OLE ダイアログ ボックスとクラスが処理されるタスクを一覧表示します。  OLE の動作をカスタマイズするために使用されるダイアログ ボックスおよび構造体の詳細については [MFC の参照](../mfc/mfc-desktop-applications.md)を参照してください。  
  
 *オブジェクトの挿入*  
 このダイアログ ボックスは、ユーザーが複合ドキュメントに新しく作成または既存のオブジェクトを挿入できるようにします。  また、項目ようにアイコンを表示することもできます。また、変更アイコンのコマンド ボタンを有効にする。  ユーザーが編集メニューから挿入オブジェクトを選択すると、このダイアログ ボックスを表示します。  このダイアログ ボックスを表示するには [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) クラスを使用します。  それ自体に MDI アプリケーションを挿入できないことに注意してください。  コンテナーとサーバーのアプリケーションは、それ自体には、SDI アプリケーションである挿入できません。  
  
 *形式を選択して貼り付け*  
 このダイアログ ボックスは、データを複合ドキュメントに貼り付けるときに使用する書式を制御できるようになります。  ユーザーは、アイコンとして表示するかどうかをデータ形式が、かどうかデータを埋め込みまたはリンクして選択できます。  ユーザーが編集メニューの貼り付けをクリックすると、このダイアログ ボックスを表示します。  このダイアログ ボックスを表示するには [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) クラスを使用します。  
  
 *アイコンを変更します。*  
 このダイアログ ボックスは、ユーザーがリンクされたを埋め込まれたアイテムを表すために、アイコンを表示するかを選択できるようにします。  ユーザーが編集メニューから変更アイコンをクリックするか、特別な貼り付けのアイコンをクリックすると、表示するダイアログ ボックスを変換すると、このダイアログ ボックスを示しています。  ユーザーがオブジェクトの挿入ダイアログ ボックスを開き、アイコンとして表示をクリックすると、タスクを表示します。  このダイアログ ボックスを表示するには [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) クラスを使用します。  
  
 *変換*  
 このダイアログ ボックスは、ユーザーが埋め込まれたのまたはリンク アイテムの種類を変更することができます。  たとえば、埋め込まれたなメタファイルを変更するために複合ドキュメントでメタファイルを埋め込み、後で他のアプリケーションを使用する場合は、変換のダイアログ ボックスを使用します。  次に、このダイアログ ボックスは、普通、編集メニューの *項目の型の* オブジェクトを、変換をクリックするカスケード メニューをクリックして、表示されます。  このダイアログ ボックスを表示するには [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) クラスを使用します。  例については、MFC サンプルの OLE [OCLIENT](../top/visual-cpp-samples.md)を実行します。  
  
 *リンクを編集するか、またはリンクを更新してください。*  
 編集はリンク オブジェクトのソースの情報を変更するためのダイアログ ボックスを使用してユーザーをリンクします。  更新リンク ダイアログ ボックスに現在のダイアログ ボックスのすべてのリンク アイテムのソースを確認し、編集リンク ダイアログ ボックスを必要に応じて表示されます。  ユーザーが編集メニューのリンクをクリックすると、Edit リンク ダイアログ ボックスを表示します。  更新リンク ダイアログ ボックスは、普通、複合ドキュメントを最初に開いたときに表示されます。  ダイアログ ボックスを表示する [COleUpdateDialog](../Topic/COleUpdateDialog%20Class.md) クラス [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) を使用してください。  
  
 *使用するサーバー応答しない*  
 サーバーが使用中のダイアログ ボックスは、サーバーが別のユーザーまたはタスクで使用されているため、項目をアクティブにする場合は、サーバーが要求を処理して現在存在しない場合、通常、表示されます。  サーバー応答ダイアログ ボックスは、サーバーがアクティベーション要求に応答も表示されます。  これらのダイアログ ボックスは、OLE **IMessageFilter**インターフェイスの実装に基づいて `COleMessageFilter`で表示され、アクティベーション要求を再度行うにはかどうかを決定できます。  このダイアログ ボックスを表示するには [COleBusyDialog](../mfc/reference/colebusydialog-class.md) クラスを使用します。  
  
## 参照  
 [ダイアログ ボックス](../mfc/dialog-boxes.md)   
 [ダイアログ ボックスの有効期間](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)