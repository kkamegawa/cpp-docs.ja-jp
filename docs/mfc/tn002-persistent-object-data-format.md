---
title: TN002:永続的なオブジェクトのデータ形式
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 6d64799dc17b4b3ddc5c455333b10282e4748b09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306195"
---
# <a name="tn002-persistent-object-data-format"></a>TN002:永続的なオブジェクトのデータ形式

ここでは、ファイルに格納されるときに、永続的な C++ オブジェクトと、オブジェクトのデータの形式をサポートする MFC ルーチンについて説明します。 これでクラスにのみ適用されます、 [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)と[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)マクロ。

## <a name="the-problem"></a>問題を

永続的なデータの MFC 実装では、1 つの連続するパーツ ファイルの多数のオブジェクトのデータを格納します。 オブジェクトの`Serialize`メソッドは、オブジェクトのデータをコンパクトなバイナリ形式に変換します。

実装の保証を使用して、すべてのデータが同じ形式で保存、 [CArchive クラス](../mfc/reference/carchive-class.md)します。 使用して、`CArchive`翻訳者としてのオブジェクト。 このオブジェクトを呼び出すまでは作成時からが解決しない[CArchive::Close](../mfc/reference/carchive-class.md#close)します。 このメソッドを呼び出せませんプログラマによって明示的にまたは暗黙的に、デストラクターでプログラムを含むスコープの終了時、`CArchive`します。

この注の実装を記述する、`CArchive`メンバー [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject)と[CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject)します。 Arcobj.cpp との主な実装のこれらの関数コードを検索するは`CArchive`Arccore.cpp でします。 ユーザー コードは呼び出しません`ReadObject`と`WriteObject`直接します。 代わりに、これらのオブジェクトは、ストリームのマクロによって自動的に生成される特定のクラス タイプ セーフな挿入と抽出演算子によって使用されます。 次のコードはどのように`WriteObject`と`ReadObject`は暗黙的に呼び出されます。

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>オブジェクトを (CArchive::WriteObject) ストアに保存します。

メソッド`CArchive::WriteObject`オブジェクトの再構築に使用されるヘッダーのデータを書き込みます。 このデータは、2 つの部分で構成されています: オブジェクトとオブジェクトの状態の種類。 このメソッドは、(循環のポインターを含む)、そのオブジェクトへのポインターの数に関係なく、コピーは 1 つだけが保存されるように書き出されるオブジェクトの id を維持する責任を負いますもできます。

(挿入) を保存し、いくつか「マニフェスト定数です」に依存 (解凍) オブジェクトを復元する。 バイナリに格納され、アーカイブ (メモ"w"プレフィックスが 16 ビットの数を示します) に重要な情報を提供する値を次に示します。

|タグ|説明|
|---------|-----------------|
|wNullTag|NULL オブジェクト ポインター (0) を使用します。|
|wNewClassTag|次のクラスの説明はこのアーカイブ コンテキスト (-1) に新しいことを示します。|
|wOldClassTag|読み取られるオブジェクトのクラスは、このコンテキスト (0x8000) で発生することを示します。|

オブジェクトを格納するときに、アーカイブを保持する[CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (、 *m_pStoreMap*) 格納されているオブジェクトから 32 ビットの永続的な識別子 (PID) へのマッピングであります。 PID は、すべての一意のオブジェクトと、アーカイブのコンテキストに保存されているすべての一意のクラス名に割り当てられます。 この pid は順番に 1 から始まります。 これらの Pid 有意性、アーカイブの対象外を持たず、具体的には、レコード番号またはその他の識別情報項目と混同しないように。

`CArchive`クラス、Pid は 32 ビットは始まりません 16 ビットとして 0x7ffe でない限り、します。 大規模な Pid は、32 ビットの PID を続けて 0x7FFF として記述されます。 これにより、以前のバージョンで作成されたプロジェクトとの互換性を維持します。

Null チェックが行われます (通常は、グローバル挿入演算子を使用して) をアーカイブするオブジェクトを保存する要求が行われる[CObject](../mfc/reference/cobject-class.md)ポインター。 ポインターが NULL の場合、 *wNullTag*アーカイブ ストリームに挿入されます。

ポインターが NULL でないし、シリアル化できるかどうか (クラス、`DECLARE_SERIAL`クラス)、コードのチェック、 *m_pStoreMap*オブジェクトが既に保存されているかどうかを確認します。 場合は、コードは、アーカイブ ストリームに、そのオブジェクトに関連付けられている 32 ビットの PID を挿入します。

考慮すべき 2 つの可能性がある場合は、オブジェクトが保存されていない: オブジェクトとオブジェクトの正確な型 (つまり、クラス) の両方がこのアーカイブ コンテキストに新しいまたはオブジェクトが既に正確な型のいずれか。 種類が表示されているかどうかを判断するコードのクエリ、 *m_pStoreMap*の[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)と一致するオブジェクト、`CRuntimeClass`保存されているオブジェクトに関連付けられているオブジェクト。 一致がある場合`WriteObject`ビットであるタグを挿入`OR`の*wOldClassTag*とこのインデックス。 場合、`CRuntimeClass`はこのアーカイブ コンテキストに新しい`WriteObject`新しい PID をそのクラスに割り当てられ、前に、アーカイブ内に挿入、 *wNewClassTag*値。

このクラスの記述子を使用して、アーカイブに挿入して、`CRuntimeClass::Store`メソッド。 `CRuntimeClass::Store` クラス (下記参照) のスキーマの数と、クラスの ASCII テキスト名を挿入します。 ASCII テキスト名の使用によって、アプリケーション間で、アーカイブの一意性が保証されるしないことに注意してください。 そのため、破損を防ぐために、データ ファイルをタグ付けする必要があります。 次のクラス情報の挿入、アーカイブに配置オブジェクトを*m_pStoreMap*し呼び出します、`Serialize`クラスに固有のデータを挿入するメソッド。 オブジェクトを配置すること、 *m_pStoreMap*呼び出す前に`Serialize`オブジェクトの複数のコピーがストアに保存されていることを防ぎます。

呼び出す必要がある場合、最初の呼び出し元 (通常はオブジェクトのネットワークのルート) に戻って、 [CArchive::Close](../mfc/reference/carchive-class.md#close)します。 実行する予定の場合[CFile](../mfc/reference/cfile-class.md)、操作を呼び出す必要があります、`CArchive`メソッド[フラッシュ](../mfc/reference/carchive-class.md#flush)アーカイブの破損を回避します。

> [!NOTE]
>  この実装は、アーカイブ コンテキストごとインデックス数が 0x3FFFFFFE ハード制限です。 この数は 1 つのアーカイブに保存できるクラスと一意のオブジェクトの最大数を表しますが、1 つのディスク ファイルは、アーカイブのコンテキストの無制限の数を持つことができます。

## <a name="loading-objects-from-the-store-carchivereadobject"></a>ストア (CArchive::ReadObject) からオブジェクトの読み込み

オブジェクトを使用して (の抽出) を読み込み、`CArchive::ReadObject`メソッドの逆で、`WriteObject`します。 同様`WriteObject`、`ReadObject`ユーザー コードが直接は呼び出さないユーザー コードはタイプ セーフな抽出演算子を呼び出す必要があります`ReadObject`備えた`CRuntimeClass`します。 これにより、抽出操作の型の整合性が保証されます。

以降、`WriteObject`実装には、1 から始まる増加の Pid が割り当てられている (0 は、NULL オブジェクトとして定義済み)、`ReadObject`実装は、アーカイブのコンテキストの状態を維持するために配列を使用できます。 場合、PID は読み取り専用ストアからの現在の上限よりも大きい場合は、PID、 *m_pLoadArray*、`ReadObject`新しいオブジェクト (またはクラスの説明) に従うことを認識します。

## <a name="schema-numbers"></a>スキーマの番号

スキーマの数、クラスに割り当てられるときに、`IMPLEMENT_SERIAL`クラスのメソッドが発生した、クラスの実装の「バージョン」です。 回数の合計が、特定のオブジェクトは永続的な (オブジェクトのバージョンと通常呼ばれる)、スキーマが、クラスの実装を示します。

長期にわたって、同じクラスの複数の異なる実装を管理する場合は、インクリメント、スキーマ オブジェクトの編集した後、`Serialize`の古いバージョンを使用して格納されているオブジェクトを読み込むことができるコードを記述するメソッドの実装が有効にします。実装。

`CArchive::ReadObject`メソッドがスローされます、 [CArchiveException](../mfc/reference/carchiveexception-class.md)クラスの説明をメモリ内のスキーマの数とは異なる、永続的なストアでのスキーマの数に到達したとき。 この例外から回復する簡単ではありません。

使用することができます`VERSIONABLE_SCHEMA`と組み合わせる (ビット演算**または**) して、この例外がスローされているスキーマ バージョン。 使用して`VERSIONABLE_SCHEMA`、コード、適切な処置を実行できるその`Serialize`関数からの戻り値をチェックして[CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)します。

## <a name="calling-serialize-directly"></a>呼び出し元を直接シリアル化します。

多くの場合の一般的なオブジェクトのアーカイブ スキーマのオーバーヘッド`WriteObject`と`ReadObject`必要はありません。 これは、データのシリアル化の一般的なケースを[CDocument](../mfc/reference/cdocument-class.md)します。 ここで、`Serialize`のメソッド、`CDocument`抽出または挿入演算子ではなく、直接と呼ばれます。 ドキュメントの内容は、一般的なオブジェクト アーカイブ スキームを使用さらに可能性があります。

呼び出す`Serialize`次の長所と短所を直接には。

- オブジェクトがシリアル化後または前にアーカイブに追加のバイトが追加されません。 これだけでなく、保存したデータをより小さい場合は、によりが実装することができます`Serialize`ファイル形式のいずれかを処理できるルーチン。

- MFC が調整されたため、`WriteObject`と`ReadObject`の実装と関連するコレクションはリンクされませんをアプリケーションに別の目的より一般的なオブジェクトのアーカイブ スキームが必要でない限りです。

- コードを古いスキーマ番号から復元する必要はありません。 これにより、ドキュメントのシリアル化コードは、エンコード スキーマ番号、ファイル形式のバージョン番号、またはあらゆる識別番号を担当する、データ ファイルの先頭に使用します。

- 任意のオブジェクトを直接呼び出しでは、シリアル化を`Serialize`は使用しないで`CArchive::GetObjectSchema`またはする必要があります (UINT)-1 の戻り値のハンドルを示す、バージョンが不明でした。

`Serialize`と呼ばれますが、ドキュメントに直接ことはできません、通常はその親ドキュメントへの参照をアーカイブするドキュメントのサブオブジェクトの。 これらのオブジェクト必要があるポインターがコンテナーのドキュメントを明示的にまたは使用する必要があります[CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject)にマップする関数、`CDocument`これらの戻りポインターをアーカイブする前に、PID へのポインター。

エンコード バージョンと呼び出すときに情報を自分でクラスが前述のように、`Serialize`直接、古いファイルとの下位互換性を維持しながら、後で、形式を変更することを有効にします。 `CArchive::SerializeClass`直接オブジェクトをシリアル化する前に、または基底クラスを呼び出す前に、関数を明示的に呼び出すことができます。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
