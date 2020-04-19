---
title: CObject クラス
ms.date: 11/04/2016
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: 515c4e90ee6ab77a6c7c1ae108393ea1aafb7c17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388320"
---
# <a name="cobject-class"></a>CObject クラス

MFC ライブラリの重要な基底クラスです。

## <a name="syntax"></a>構文

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CObject::CObject](#cobject)|既定のコンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CObject::AssertValid](#assertvalid)|このオブジェクトの整合性を検証します。|
|[CObject::Dump](#dump)|このオブジェクトの診断ダンプを生成します。|
|[CObject::GetRuntimeClass](#getruntimeclass)|返します、`CRuntimeClass`このオブジェクトのクラスに対応する構造体。|
|[CObject::IsKindOf](#iskindof)|特定のクラスをこのオブジェクトのリレーションシップをテストします。|
|[CObject::IsSerializable](#isserializable)|このオブジェクトをシリアル化できるかどうかを確認するかをテストします。|
|[Cobject::serialize](#serialize)|読み込みまたはアーカイブをオブジェクトを格納します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CObject::operator delete](#operator_delete)|特別な **delete** 演算子。|
|[CObject::operator new](#operator_new)|特別な **new** 演算子。|

## <a name="remarks"></a>Remarks

などのライブラリのクラスだけでなく、ルートとして機能します`CFile`と`CObList`がも記述するクラス。 `CObject` などの基本的なサービスを提供します。

- シリアル化のサポート

- ランタイム クラス情報

- オブジェクトの診断出力

- コレクション クラスとの互換性

なお`CObject`多重継承をサポートしていません。 派生クラスには、1 つだけを指定できる`CObject`基本クラス、およびを`CObject`階層の一番左にある必要があります。 許される、ただし、構造があると非- `CObject`-右側の多重継承の分岐内のクラスを派生します。

主なメリットを実感`CObject`派生クラスの実装と宣言で省略可能なマクロの一部を使用する場合。

最初のレベルのマクロ[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)と[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)実行時に、クラス名と、階層内の位置にアクセスを許可します。 さらに、これには、により、意味のある診断ダンプします。

2 番目のレベルのマクロ[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)と[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)第 1 レベルのマクロのすべての機能を追加し、"シリアル化されるオブジェクト"と「アーカイブ」です有効にする。

一般に、Microsoft Foundation classes と C++ のクラスを派生し、`CObject`を使用する方法については、[CObject の使い方](../../mfc/using-cobject.md)と[シリアル化](../../mfc/serialization-in-mfc.md)を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`CObject`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="assertvalid"></a>  CObject::AssertValid

このオブジェクトの整合性を検証します。

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Remarks

`AssertValid` 内部状態をチェックして、このオブジェクトの有効性チェックを実行します。 ライブラリのデバッグ バージョンで`AssertValid`アサートし、アサーションが失敗した行番号とファイル名を一覧表示するメッセージをプログラムを終了したがって可能性があります。

オーバーライドする独自のクラスを記述するときに、`AssertValid`自分や他のユーザー クラスのための診断サービスを提供する関数。 オーバーライドされた`AssertValid`呼び出しは、通常、`AssertValid`派生クラスに固有のデータ メンバーを確認する前に、基底クラスの関数。

`AssertValid`は、 **const**関数の場合は、テスト中に、オブジェクトの状態を変更する許可されていません。 派生クラス`AssertValid`関数が例外をスローする必要がありますが、無効なオブジェクトのデータを検出するかどうかではなくをアサートします。

「有効」の定義は、オブジェクトのクラスに依存します。 原則として、関数が「簡易チェック」を実行します。 オブジェクトに他のオブジェクトへのポインターが含まれている場合ことを確認するかどうか、ポインターが null でなく、有効性、ポインターによって参照されるオブジェクトに対するテストを実行する必要があります。

### <a name="example"></a>例

すべての`CObject`の例で使用されている`CAge`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)を参照してください。

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

別の例では、次を参照してください。 [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)します。

##  <a name="cobject"></a>  CObject::CObject

これらの関数は、標準`CObject`コンス トラクター。

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>パラメーター

*objectSrc*<br/>
別の参照 `CObject`

### <a name="remarks"></a>Remarks

既定のバージョンは、派生クラスのコンス トラクターによって自動的に呼び出されます。

クラスがシリアル化可能な場合 (IMPLEMENT_SERIAL マクロが組み込まれている場合)、クラス宣言に既定のコンス トラクター (引数なしのコンス トラクター) が必要です。 既定のコンス トラクターが必要ない場合、private を宣言または「空」のコンス トラクターを宣言します。 詳細については、[CObject の使い方](../../mfc/using-cobject.md) を参照してください。

標準 C++ 既定クラスのコピー コンス トラクターは、メンバー間でコピーします。 プライベートのプレゼンス`CObject`コピー コンス トラクターで、クラスのコピー コンス トラクターが必要なは利用できない場合、コンパイラ エラー メッセージが保証されます。 クラスには、この機能が必要な場合にそのため、コピー コンス トラクターを提供する必要があります。

### <a name="example"></a>例

すべての`CObject`の例で使用されている`CAge`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist) を参照してください。

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>  CObject::Dump

オブジェクトの内容をダンプする[CDumpContext](../../mfc/reference/cdumpcontext-class.md)オブジェクト。

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
通常、ダンプの診断ダンプ コンテキスト`afxDump`します。

### <a name="remarks"></a>Remarks

オーバーライドする独自のクラスを記述するときに、`Dump`自分や他のユーザー クラスのための診断サービスを提供する関数。 オーバーライドされた`Dump`呼び出しは、通常、`Dump`派生クラスに固有のデータ メンバーを印刷する前に、基底クラスの関数。 `CObject::Dump` クラスで使用する場合は、クラス名を出力、`IMPLEMENT_DYNAMIC`または IMPLEMENT_SERIAL マクロ。

> [!NOTE]
>  `Dump`関数は、その出力の最後に改行文字を印刷する必要があります。

`Dump` 呼び出しは、Microsoft Foundation Class ライブラリのデバッグ バージョンでのみ意味します。 呼び出し、関数の宣言と関数の実装を角かっこは **#ifdef _DEBUG** /  `#endif`条件付きコンパイル ステートメント。

`Dump`は、 **const**関数の場合は、ダンプ中に、オブジェクトの状態を変更する許可されていません。

[CDumpContext 挿入 (<<) 演算子](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)呼び出し`Dump`ときに、`CObject`ポインターを挿入します。

`Dump` オブジェクトのダンプを「非循環」のみを許可します。 など、オブジェクトの一覧をダンプすることができますが、一方のオブジェクトが、リスト自体の場合は、スタックがオーバーフロー最終的にします。

### <a name="example"></a>例

すべての`CAge`の例で使用されている`CObject`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)を参照してください。

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass

返します、`CRuntimeClass`このオブジェクトのクラスに対応する構造体。

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>戻り値

ポインター、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)構造体がこのオブジェクトのクラスに対応することはありません**NULL**します。

### <a name="remarks"></a>Remarks

1 つである`CRuntimeClass`構造`CObject`-クラスを派生します。 構造体のメンバーは次のとおりです。

- **LPCSTR m_lpszClassName** ASCII クラス名を含む null で終わる文字列。

- **int m_nObjectSize** (バイト単位)、オブジェクトのサイズ。 オブジェクトは、割り当てられたメモリを指すデータ メンバーを持っている場合はそのメモリのサイズは含まれません。

- **UINT m_wSchema**スキーマの数 (-シリアル化できないクラスの 1)。 参照してください、 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)スキーマ番号の説明についてはマクロです。

- **CObject\* (PASCAL\* m_pfnCreateObject) に関するページ ()** クラスのオブジェクトを作成する既定のコンス トラクター関数ポインター (有効なクラスは、動的作成をサポートする場合にのみ、それ**NULL**).

- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) に関するページ ()** アプリケーションは AFXDLL バージョンの MFC を動的にリンクしている場合、関数へのポインターを返す、`CRuntimeClass`基底クラスの構造体。

- **CRuntimeClass\* m_pBaseClass** 、アプリケーションが MFC へのポインターを静的にリンクされているかどうか、`CRuntimeClass`基底クラスの構造体。

この関数の使用が必要です、 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)、 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)、または[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)マクロで、クラスの実装。 それ以外の場合正しくない結果が得られます。

### <a name="example"></a>例

すべての`CAge`の例で使用されている`CObject`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)を参照してください。

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>  CObject::IsKindOf

特定のクラスをこのオブジェクトのリレーションシップをテストします。

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>パラメーター

*pClass*<br/>
ポインターを[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)構造に関連付けられている、 `CObject`-クラスを派生します。

### <a name="return-value"></a>戻り値

オブジェクトは、クラスに対応している場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

この関数をテスト*pClass*に指定したクラスのオブジェクトは、(1) か、指定したクラスから派生したクラスのオブジェクトである (2) を参照してください。 この関数の動作で宣言されたクラスに対してのみ、 [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)、 [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)、または[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)マクロ。

C++ ポリモーフィズムの機能を損なうことためには、広範囲にこの関数を使用しないでください。 代わりに、仮想関数を使用します。

### <a name="example"></a>例

すべての`CAge`の例で使用されている`CObject`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)を参照してください。

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>  CObject::IsSerializable

このオブジェクトがシリアル化の対象であるかどうかをテストします。

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>戻り値

この場合は 0 以外のオブジェクトをシリアル化することができます。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

シリアル化できるクラスの宣言を含める必要があります、 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)マクロ、および実装を含める必要があります、 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)マクロ。

> [!NOTE]
>  この関数は無効です。

### <a name="example"></a>例

すべての`CAge`の例で使用されている`CObject`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)を参照してください。

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>  CObject::operator delete

ライブラリのリリース バージョンの場合、**delete** 演算子は **new** 演算子によって割り当てられたメモリを解放します。

```
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Remarks

デバッグ バージョンでは、**delete** 演算子メモリ リークを検出するために設計された割り当て監視スキームに参加します。

コード行を使用する場合

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

実装の前に、します。CPP ファイルを次の 3 番目のバージョン**削除**使用される、割り当て済みのブロックを後でレポートをファイル名と行の数を格納します。 追加のパラメーターを指定する必要はありません。マクロがそれを対処します。

リークの検出をそれでもデバッグ モードで DEBUG_NEW を使用しない場合でも上記で説明したソース ファイルの行番号のレポート作成しなくてもします。

**new** と **delete** 演算子をオーバーライドすると、この診断機能が多少低下します。

### <a name="example"></a>例

すべての`CAge`の例で使用されている`CObject`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist) を参照してください。

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>  CObject::operator new

ライブラリのリリース バージョンでは、**new** 演算子は`malloc`と同様の方法で最適なメモリ割り当てを実行します。

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Remarks

デバッグ バージョンでは、**new**  演算子メモリ リークを検出するように設計された割り当て監視スキームに参加します。

コード行を使用する場合

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

CPP ファイルの実装の前に、 2 番目のバージョンの **new** が使用され、後で割り当て済みのブロックにでファイル名と行の数を格納します。 追加のパラメーターを指定する必要はありません。マクロがそれを対処します。

リークの検出をそれでもデバッグ モードで DEBUG_NEW を使用しない場合でも上記で説明したソース ファイルの行番号のレポート作成しなくてもします。

> [!NOTE]
>  演算子をオーバーライドする場合は、**delete** もオーバーライドする必要があります。 標準ライブラリの`_new_handler`関数を使用しないでください。

### <a name="example"></a>例

すべての`CAge`の例で使用されている`CObject`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist) を参照してください。

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>  Cobject::serialize

アーカイブに対して、このオブジェクトの読み取りまたは書き込みを行います。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

*ar*<br/>
A`CArchive`またはからにシリアル化するオブジェクト。

### <a name="remarks"></a>Remarks

オーバーライドする必要があります`Serialize`シリアル化するクラスごとにします。 オーバーライドされた`Serialize`最初に呼び出す必要があります、`Serialize`基底クラスの関数。

使用することも必要があります、 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)クラスの宣言でマクロを使用する必要があります、 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)実装ではマクロです。

[CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) または [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) を使用して、アーカイブがロード中か保存中かを判断します。

`Serialize` によって呼び出される[CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject)と[CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)します。 これらの関数が関連付けられている、`CArchive`挿入演算子 ( **< \<** ) と抽出演算子 ( **>>** )。

シリアル化の例は、[シリアル化:オブジェクトのシリアル化](../../mfc/serialization-serializing-an-object.md) を参照してください。

### <a name="example"></a>例

すべての`CAge`の例で使用されている`CObject`クラスのリストについては、[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)を参照してください。

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)
