---
title: CAtlMap クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 1821532a4d5a3078202f180273b02945b8d8e4ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260611"
---
# <a name="catlmap-class"></a>CAtlMap クラス

このクラスは、作成して、map オブジェクトを管理するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

#### <a name="parameters"></a>パラメーター

*K*<br/>
キーの要素の型。

*V*<br/>
要素の値の型。

*KTraits*<br/>
コピーまたは主要な要素を移動するために使用するコードです。 参照してください[CElementTraits クラス](../../atl/reference/celementtraits-class.md)の詳細。

*VTraits*<br/>
コピーまたは値の要素を移動するために使用するコードです。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|キーが入力引数として渡されるときに使用される型|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|キーが出力引数として返されるときに使用する型。|
|[CAtlMap::VINARGTYPE](#vinargtype)|型の値が入力引数として渡されるときに使用します。|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|型の値が出力引数として渡されるときに使用します。|

### <a name="public-classes"></a>パブリック クラス

|名前|説明|
|----------|-----------------|
|[CAtlMap::CPair クラス](#cpair_class)|キーと値の要素を含むクラスです。|

### <a name="cpair-data-members"></a>CPair データ メンバー

|名前|説明|
|----------|-----------------|
|[CPair::m_key](#m_key)|重要な要素を格納するデータ メンバー。|
|[CPair::m_value](#m_value)|値の要素を格納するデータ メンバー。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|コンストラクターです。|
|[CAtlMap::~CAtlMap](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|アサートが発生する場合に、このメソッドを呼び出す、`CAtlMap`が無効です。|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|自動再ハッシュを無効にするには、このメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|自動再ハッシュを有効にするには、このメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::GetAt](#getat)|マップ内の指定位置にある要素を返すには、このメソッドを呼び出します。|
|[CAtlMap::GetCount](#getcount)|マップ内の要素の数を取得するには、このメソッドを呼び出します。|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|マップのハッシュ テーブルでビンの数を決定するには、このメソッドを呼び出します。|
|[CAtlMap::GetKeyAt](#getkeyat)|指定された位置に格納されているキーを取得するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::GetNext](#getnext)|次の要素に格納されているペアへのポインターを取得するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。|
|[CAtlMap::GetNextAssoc](#getnextassoc)|反復処理するためには、次の要素を取得します。|
|[CAtlMap::GetNextKey](#getnextkey)|次のキーを取得するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。|
|[CAtlMap::GetNextValue](#getnextvalue)|[次へ] の値を取得するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。|
|[CAtlMap::GetStartPosition](#getstartposition)|マップの反復処理を開始するには、このメソッドを呼び出します。|
|[CAtlMap::GetValueAt](#getvalueat)|指定された位置に格納されている値を取得するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::InitHashTable](#inithashtable)|ハッシュ テーブルを初期化するためには、このメソッドを呼び出します。|
|[CAtlMap::IsEmpty](#isempty)|空のマップ オブジェクトをテストするには、このメソッドを呼び出します。|
|[CAtlMap::Lookup](#lookup)|キーまたは値を検索するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::Rehash](#rehash)|Rehash にこのメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::RemoveAll](#removeall)|すべての要素を削除するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::RemoveAtPos](#removeatpos)|指定した位置にある要素を削除するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。|
|[CAtlMap::RemoveKey](#removekey)|要素を削除するには、このメソッドを呼び出して、`CAtlMap`キーが指定されたオブジェクト。|
|[CAtlMap::SetAt](#setat)|マップに要素のペアを挿入するには、このメソッドを呼び出します。|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|最適な読み込みを設定するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。|
|[CAtlMap::SetValueAt](#setvalueat)|指定された位置に格納されている値を変更するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|置き換えるか、新しい要素を追加します、`CAtlMap`します。|

## <a name="remarks"></a>Remarks

`CAtlMap` 主な要素と関連付けられた値の順序なしの配列を管理する特定の型のマッピングの配列のサポートを提供します。 大量のデータを効率的に格納し、取得できるように、ハッシュ アルゴリズムを使用して (キーと値から成る) 要素が格納されます。

*KTraits*と*VTraits*パラメーターは、特性クラスをコピーまたは要素の移動に必要な補足コードが含まれています。

代わりに`CAtlMap`によって提供される、 [CRBMap](../../atl/reference/crbmap-class.md)クラス。 `CRBMap` キー/値のペアを格納されますが、さまざまなパフォーマンスの特徴も。 キー、検索、項目を挿入する時間またはからキーを削除、`CRBMap`の注文オブジェクトでは*log (n)* ここで、 *n*要素の数です。 `CAtlMap`、注文の最悪のシナリオがありますが、通常、定数時間がかかるこれらすべての操作*n*します。 そのため、通常で`CAtlMap`が高速です。

その他の違い`CRBMap`と`CAtlMap`格納されている要素を反復処理するときに、明らかになります。 `CRBMap`要素の並べ替えられた順序でアクセスします。 `CAtlMap`要素の順序がありません、および順序を推論できません。

格納される要素の数が少ない場合は、使用を検討して、 [CSimpleMap](../../atl/reference/csimplemap-class.md)クラスの代わりにします。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="assertvalid"></a>  CAtlMap::AssertValid

アサートが発生する場合に、このメソッドを呼び出す、`CAtlMap`オブジェクトが無効です。

```
void AssertValid() const;
```

### <a name="remarks"></a>Remarks

デバッグ ビルドでこのメソッドは、アサート場合、`CAtlMap`オブジェクトが無効です。

### <a name="example"></a>例

例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="catlmap"></a>  CAtlMap::CAtlMap

コンストラクターです。

```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>パラメーター

*nBins*<br/>
格納されている要素へのポインターを提供するビンの数。 ビンの詳細については、このトピックの後半の「解説」を参照してください。

*fOptimalLoad*<br/>
最適な読み込みの比率です。

*fLoThreshold*<br/>
負荷率の下限しきい値。

*fHiThreshold*<br/>
負荷率の上限しきい値。

*nBlockSize*<br/>
ブロック サイズ。

### <a name="remarks"></a>Remarks

`CAtlMap` 最初に、キーのハッシュ アルゴリズムを使用してインデックスを作成するには、その格納されている要素のすべてを参照します。 このインデックスは、格納されている要素へのポインターを含む"bin"を参照します。 ビンが既に使用されている、後続の要素にアクセスするリンクされたリストが作成されます。 目的の要素に直接アクセスするよりも遅くなりますが、リスト内の移動と、したがって、マップの構造がパフォーマンスとストレージ要件のバランスを取る必要があります。 ほとんどの場合、適切な結果を提供する既定のパラメーターが選択されました。

読み込みの比率は、マップ オブジェクト内に格納されている要素の数のビンの数の比率です。 マップの構造が再計算するとき、 *fOptimalLoad*必要なビンの数を計算するパラメーターの値が使用されます。 使用してこの値を変更できる、 [CAtlMap::SetOptimalLoad](#setoptimalload)メソッド。

*FLoThreshold*パラメーターは、負荷の比率は、前にアクセスできる低値`CAtlMap`マップの最適なサイズを再計算されます。

*FHiThreshold*パラメーターは、負荷の比率は、前にアクセスできる上限の値、`CAtlMap`オブジェクトは、マップの最適なサイズを再計算されます。

この再計算プロセスが (再ハッシュと呼ばれます) は、既定で有効です。 大量のデータで一度に 1 つの呼び出しを入力するときに、おそらく、このプロセスを無効にする場合、 [CAtlMap::DisableAutoRehash](#disableautorehash)メソッド。 再アクティブ化、 [CAtlMap::EnableAutoRehash](#enableautorehash)メソッド。

*NBlockSize*パラメーターは、新しい要素が必要なときに割り当てられたメモリ量の測定単位です。 ブロック サイズの増加はメモリ割り当てルーチンの呼び出しを減らすためがより多くのリソースを使用します。

呼び出しでハッシュ テーブルを初期化する必要がすべてのデータを格納することができます、前に[格納する](#inithashtable)します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

##  <a name="dtor"></a>  CAtlMap::~CAtlMap

デストラクターです。

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたリソースを解放します。

##  <a name="cpair_class"></a>  CAtlMap::CPair クラス

キーと値の要素を含むクラスです。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Remarks

このクラスは、メソッドによって使用[で](#getnext)と[CAtlMap::Lookup](#lookup)マップ構造体に格納されているキーと値の要素にアクセスします。

##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash

自動再ハッシュを無効にするには、このメソッドを呼び出して、`CAtlMap`オブジェクト。

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Remarks

自動再ハッシュには、(既定である) 有効な場合は、ハッシュ テーブルでビンの数が自動的に再計算の負荷値 (配列に格納されている要素の数のビンの数の比率) が最大値または最小値を超えた場合マップの作成時に指定します。

`DisableAutoRehash` 多数の要素が追加されるマップを一度に最も役立ちます。 呼び出す方が効率的です rehashing プロセスをトリガーするたびに、制限を超えたではなく`DisableAutoRehash`、要素を追加し、最後に呼び出して、 [CAtlMap::EnableAutoRehash](#enableautorehash)します。

##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash

自動再ハッシュを有効にするには、このメソッドを呼び出して、`CAtlMap`オブジェクト。

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Remarks

自動再ハッシュには、(既定である) 有効な場合は、ハッシュ テーブルでビンの数が自動的に再計算の負荷値 (配列に格納されている要素の数のビンの数の比率) が最大値または最小値を超えた場合マップの作成時に指定します。

`EnableAutoRefresh` 呼び出しの後に、最もよく使用[CAtlMap::DisableAutoRehash](#disableautorehash)します。

##  <a name="getat"></a>  CAtlMap::GetAt

マップ内の指定位置にある要素を返すには、このメソッドを呼び出します。

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

*key*<br/>
マップのキーの種類を指定するテンプレート パラメーター。

*value*<br/>
マップの値の型を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

マップに格納されているキー/値要素の現在のペアにポインターを返します。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生*pos*が NULL です。

##  <a name="getcount"></a>  CAtlMap::GetCount

マップ内の要素の数を取得するには、このメソッドを呼び出します。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>戻り値

マップ オブジェクト内の要素の数を返します。 1 つの要素は、キー/値ペアです。

### <a name="example"></a>例

例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize

マップのハッシュ テーブルでビンの数を決定するには、このメソッドを呼び出します。

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>戻り値

ハッシュ テーブルには、ビンの数を返します。 参照してください[CAtlMap::CAtlMap](#catlmap)説明します。

##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt

指定された位置に格納されているキーを取得するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

### <a name="return-value"></a>戻り値

指定された位置に格納されているキーへの参照を返します、`CAtlMap`オブジェクト。

### <a name="example"></a>例

例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="getnext"></a>  CAtlMap::GetNext

次の要素に格納されているペアへのポインターを取得するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

### <a name="return-value"></a>戻り値

マップに格納されているキー/値要素の次の組み合わせにポインターを返します。 *Pos*位置カウンターは各呼び出しの後に更新されます。 取得した要素が、マップ内の最後の場合*pos* NULL に設定されます。

##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc

反復処理するためには、次の要素を取得します。

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

*key*<br/>
マップのキーの種類を指定するテンプレート パラメーター。

*value*<br/>
マップの値の型を指定するテンプレート パラメーター。

### <a name="remarks"></a>Remarks

*Pos*位置カウンターは各呼び出しの後に更新されます。 取得した要素が、マップ内の最後の場合*pos* NULL に設定されます。

##  <a name="getnextkey"></a>  CAtlMap::GetNextKey

次のキーを取得するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

### <a name="return-value"></a>戻り値

マップ内の次のキーへの参照を返します。

### <a name="remarks"></a>Remarks

現在の位置のカウンターの更新*pos*します。マップのエントリがある場合、位置のカウンターは NULL に設定します。

##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue

[次へ] の値を取得するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

### <a name="return-value"></a>戻り値

マップで、[次へ] の値への参照を返します。

### <a name="remarks"></a>Remarks

現在の位置のカウンターの更新*pos*します。マップのエントリがある場合、位置のカウンターは NULL に設定します。

### <a name="example"></a>例

例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition

マップの反復処理を開始するには、このメソッドを呼び出します。

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>戻り値

マップが空の場合に、開始位置、または NULL が返されますを返します。

### <a name="remarks"></a>Remarks

値の位置を返すことによって、マップの反復処理を開始するには、このメソッドの呼び出しに渡すことができます、`GetNextAssoc`メソッド。

> [!NOTE]
>  繰り返しシーケンスは予測できません。

### <a name="example"></a>例

例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="getvalueat"></a>  CAtlMap::GetValueAt

指定された位置に格納されている値を取得するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

### <a name="return-value"></a>戻り値

指定された位置に格納されている値への参照を返します、`CAtlMap`オブジェクト。

##  <a name="inithashtable"></a>  CAtlMap::InitHashTable

ハッシュ テーブルを初期化するためには、このメソッドを呼び出します。

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>パラメーター

*nBins*<br/>
ハッシュ テーブルで使用されるビンの数。 参照してください[CAtlMap::CAtlMap](#catlmap)説明します。

*bAllocNow*<br/>
フラグの表示メモリを割り当てる必要がある場合。

### <a name="return-value"></a>戻り値

初期化が成功、TRUE を返しますを返します。

### <a name="remarks"></a>Remarks

`InitHashTable` すべての要素がハッシュ テーブルに保存される前に呼び出す必要があります。  このメソッドが明示的に呼び出されない場合は呼び出すことが自動的に要素が追加で指定された bin カウントを使用して初めて、`CAtlMap`コンス トラクター。  指定された新しいビンの数を使用してマップを初期化は、それ以外の場合、 *nBins*パラメーター。

場合、 *bAllocNow*パラメーターが false で、必須では最初になるまで、ハッシュ テーブルに必要なメモリを割り当てられませんが。 マップを使用する場合は、特定されていない場合に役立ちます。 ことができます。

### <a name="example"></a>例

例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="isempty"></a>  CAtlMap::IsEmpty

空のマップ オブジェクトをテストするには、このメソッドを呼び出します。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>戻り値

かどうか、map が空、FALSE それ以外の場合は TRUE を返します。

##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE

キーが入力引数として渡されるときに使用される型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE

キーが出力引数として返されるときに使用する型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="lookup"></a>  CAtlMap::Lookup

キーまたは値を検索するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索する要素を識別するキーを指定します。

*value*<br/>
検索する値を受け取る変数。

### <a name="return-value"></a>戻り値

キーが見つかった場合は true、メソッドの最初のフォームを返します。 2 番目と 3 番目のフォームへのポインターを返す、 [CPair](#cpair_class)への呼び出しの位置として使用できる[で](#getnext)という具合です。

### <a name="remarks"></a>Remarks

`Lookup` ハッシュ アルゴリズムを使用して、すばやく正確に特定のキーのパラメーターに一致するキーを含むマップの要素を検索します。

##  <a name="operator_at"></a>  CAtlMap::operator \[\]

置き換えるか、新しい要素を追加します、`CAtlMap`します。

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
追加または置換する要素のキー。

### <a name="return-value"></a>戻り値

指定したキーに関連付けられている値への参照を返します。

### <a name="example"></a>例

キーが既に存在する場合は、要素が置き換えられます。 キーが存在しない場合は、新しい要素が追加されます。 例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="rehash"></a>  CAtlMap::Rehash

Rehash にこのメソッドを呼び出して、`CAtlMap`オブジェクト。

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>パラメーター

*nBins*<br/>
ハッシュ テーブルで使用する新しいビン数。 参照してください[CAtlMap::CAtlMap](#catlmap)説明します。

### <a name="remarks"></a>Remarks

場合*nBins*は 0 です。`CAtlMap`マップと最適な読み込みの設定要素の数に基づく妥当な数を計算します。 Rehashing プロセスは自動に通常場合[CAtlMap::DisableAutoRehash](#disableautorehash)が呼び出されると、このメソッドが実行するために必要なサイズを変更します。

##  <a name="removeall"></a>  CAtlMap::RemoveAll

すべての要素を削除するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Remarks

消去、`CAtlMap`要素を格納するために使用するメモリを解放するオブジェクト。

##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos

指定した位置にある要素を削除するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

### <a name="remarks"></a>Remarks

指定した位置に格納されているキー/値ペアを削除します。 要素の格納に使用されるメモリは解放されます。 によって参照される位置*pos* 、無効になり、マップ内の他の要素の位置が有効では必ずしも同じ順序を保持します。

##  <a name="removekey"></a>  CAtlMap::RemoveKey

要素を削除するには、このメソッドを呼び出して、`CAtlMap`キーが指定されたオブジェクト。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
削除する要素のペアに対応するキー。

### <a name="return-value"></a>戻り値

キーが見つかったと削除された、失敗した場合は FALSE のかどうかは TRUE を返します。

### <a name="example"></a>例

例をご覧ください[CAtlMap::CAtlMap](#catlmap)します。

##  <a name="setat"></a>  CAtlMap::SetAt

マップに要素のペアを挿入するには、このメソッドを呼び出します。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
追加するキー値、`CAtlMap`オブジェクト。

*value*<br/>
追加する値、`CAtlMap`オブジェクト。

### <a name="return-value"></a>戻り値

キー/値要素のペアの位置を返します、`CAtlMap`オブジェクト。

### <a name="remarks"></a>Remarks

`SetAt` 一致するキーが見つかった場合は、既存の要素を置き換えます。 キーが見つからない場合は、新しいキー/値ペアが作成されます。

##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad

最適な読み込みを設定するには、このメソッドを呼び出して、`CAtlMap`オブジェクト。

```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>パラメーター

*fOptimalLoad*<br/>
最適な読み込みの比率です。

*fLoThreshold*<br/>
負荷率の下限しきい値。

*fHiThreshold*<br/>
負荷率の上限しきい値。

*bRehashNow*<br/>
ハッシュ テーブルを再計算する場合を示すフラグします。

### <a name="remarks"></a>Remarks

このメソッドの最適な読み込みの値を再定義、`CAtlMap`オブジェクト。 参照してください[CAtlMap::CAtlMap](#catlmap)さまざまなパラメーターの詳細についてはします。 場合*bRehashNow*が true の場合とは、要素の数が最小値と最大値は、ハッシュ テーブルは再計算されます。

##  <a name="setvalueat"></a>  CAtlMap::SetValueAt

指定された位置に格納されている値を変更するには、このメソッドを呼び出す、`CAtlMap`オブジェクト。

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
以前の呼び出しによって返される位置カウンター [CAtlMap::GetNextAssoc](#getnextassoc)または[CAtlMap::GetStartPosition](#getstartposition)します。

*value*<br/>
追加する値、`CAtlMap`オブジェクト。

### <a name="remarks"></a>Remarks

指定された位置に格納されている値を変更、`CAtlMap`オブジェクト。

##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE

型の値が入力引数として渡されるときに使用します。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE

型の値が出力引数として渡されるときに使用します。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

##  <a name="m_key"></a>  CAtlMap::CPair::m_key

重要な要素を格納するデータ メンバー。

```
const K m_key;
```

### <a name="parameters"></a>パラメーター

*K*<br/>
キーの要素の型。

##  <a name="m_value"></a>  CAtlMap::CPair::m_value

値の要素を格納するデータ メンバー。

```
V  m_value;
```

### <a name="parameters"></a>パラメーター

*V*<br/>
要素の値の型。

## <a name="see-also"></a>関連項目

[マーキーのサンプル](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV サンプル](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
