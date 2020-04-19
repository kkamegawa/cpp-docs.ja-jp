---
title: CComObjectRootEx クラス
ms.date: 11/04/2016
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497043"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx クラス

このクラスは、非集計と集計されたオブジェクトの両方のオブジェクト参照カウント管理を処理するメソッドを提供します。

## <a name="syntax"></a>構文

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>パラメーター

*ThreadModel*<br/>
目的のスレッド処理モデルを実装するメソッドを持つクラス。 *Threadmodel*を[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)、または[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)に設定することによって、スレッドモデルを明示的に選択できます。 *Threadmodel*を[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)または[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)に設定することにより、サーバーの既定のスレッドモデルを受け入れることができます。

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|コンストラクターです。|
|[InternalAddRef](#internaladdref)|非集計オブジェクトの参照カウントをインクリメントします。|
|[InternalRelease](#internalrelease)|非集計オブジェクトの参照カウントをデクリメントします。|
|[制限](#lock)|スレッドモデルがマルチスレッドの場合、はクリティカルセクションオブジェクトの所有権を取得します。|
|[ロック](#unlock)|スレッドモデルがマルチスレッドの場合、はクリティカルセクションオブジェクトの所有権を解放します。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase メソッド

|||
|-|-|
|[FinalConstruct](#finalconstruct)|クラスでをオーバーライドして、オブジェクトに必要な初期化を実行します。|
|[FinalRelease](#finalrelease)|クラスでをオーバーライドして、オブジェクトに必要なクリーンアップを実行します。|
|[OuterAddRef](#outeraddref)|集計されたオブジェクトの参照カウントをインクリメントします。|
|[OuterQueryInterface](#outerqueryinterface)|集計された`IUnknown`オブジェクトの外側にデリゲートします。|
|[OuterRelease](#outerrelease)|集計されたオブジェクトの参照カウントをデクリメントします。|

### <a name="static-functions"></a>静的関数

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|非集計オブジェクトのにデリゲートします。 `IUnknown`|
|[ObjectMain](#objectmain)|オブジェクトマップに示されている派生クラスのモジュールの初期化中および終了時に呼び出されます。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_dwRef](#m_dwref)|で`m_pOuterUnknown`は、共用体の一部です。 `AddRef` および`Release`の参照カウントを保持するためにオブジェクトが集約されていない場合に使用されます。|
|[m_pOuterUnknown](#m_pouterunknown)|で`m_dwRef`は、共用体の一部です。 オブジェクトが集計され、外側の不明へのポインターを保持するときに使用されます。|

## <a name="remarks"></a>Remarks

`CComObjectRootEx`非集計と集計されたオブジェクトの両方のオブジェクト参照カウント管理を処理します。 オブジェクトが集計されていない場合、オブジェクト参照カウントを保持し、オブジェクトが集計されている場合は、外側の unknown へのポインターを保持します。 集計オブジェクト`CComObjectRootEx`の場合、メソッドを使用して、構築する内部オブジェクトのエラーを処理したり、内部インターフェイスが解放されたとき、または内部オブジェクトが削除されたときに外部オブジェクトを削除から保護したりできます。

COM サーバーを実装するクラスは、または`CComObjectRootEx` [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)から継承する必要があります。

クラス定義で[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)マクロが指定されている場合、ATL `CComPolyObject<CYourClass>`は`IClassFactory::CreateInstance`が呼び出されたときにのインスタンスを作成します。 作成時に、[外側の不明] の値がチェックされます。 NULL の場合は、 `IUnknown`非集計オブジェクトに対してが実装されます。 外側の unknown が NULL でない場合`IUnknown` 、は集計オブジェクトに対して実装されます。

クラスで DECLARE_POLY_AGGREGATABLE マクロが指定されていない場合、ATL は`CAggComObject<CYourClass>` 、集計されたオブジェクトまた`CComObject<CYourClass>`はのインスタンスを非集計オブジェクト用に作成します。

を使用する利点`CComPolyObject`は、集計されたケース`CComObject`と非集計ケースを処理するためにとの両方`CComAggObject`のモジュールを使用しないことです。 1つ`CComPolyObject`のオブジェクトが両方のケースを処理します。 したがって、モジュールには、vtable のコピーと関数のコピーが1つだけ存在します。 Vtable が大きい場合は、モジュールのサイズを大幅に減らすことができます。 ただし、vtable が小さい場合、を使用`CComPolyObject`する`CComAggObject`と、と`CComObject`のように集計または非集計オブジェクトに対して最適化されていないため、モジュールサイズが少し大きくなります。

オブジェクトが集計されている場合、[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) `CComAggObject`は`CComPolyObject`またはによって実装されます。 これら`QueryInterface`のクラスは`OuterAddRef`、 `AddRef`、 `Release` 、および`CComObjectRootEx`を呼び出して、不明な外側のに転送します。 `OuterQueryInterface` `OuterRelease` 通常、クラスで`CComObjectRootEx::FinalConstruct`をオーバーライドして集計オブジェクトを作成し、を`CComObjectRootEx::FinalRelease`オーバーライドして集計されたオブジェクトをすべて解放します。

オブジェクトが集計されてい`IUnknown`ない場合、 `CComObject`は`CComPolyObject`またはによって実装されます。 `QueryInterface`この場合、、 `AddRef`、および`Release`へ`CComObjectRootEx`の呼び出しは、 `InternalAddRef`実際の`InternalQueryInterface`操作を実行`InternalRelease`するために、、、およびに委任されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx

コンストラクターは、参照カウントを0に初期化します。

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

派生クラスでこのメソッドをオーバーライドすると、オブジェクトに必要な初期化を実行できます。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、標準エラーの HRESULT 値の1つを返します。

### <a name="remarks"></a>Remarks

既定では`CComObjectRootEx::FinalConstruct` 、は単に S_OK を返します。

クラスのコンストラクターではなく、 `FinalConstruct`で初期化を実行すると、次のような利点があります。

- コンストラクターから状態コードを返すことはできませんが、の`FinalConstruct`戻り値を使用して HRESULT を返すことができます。 クラスのオブジェクトが ATL によって提供される標準のクラスファクトリを使用して作成されている場合、この戻り値は COM クライアントに反映され、詳細なエラー情報を提供することができます。

- 仮想関数をクラスのコンストラクターから呼び出すことはできません。 クラスのコンストラクターから仮想関数を呼び出すと、継承階層のその時点で定義されているように、関数の呼び出しが静的に解決されます。 純粋仮想関数を呼び出すと、リンカーエラーが発生します。

   クラスは、継承階層の最派生クラスではありません。このクラスは、その機能の一部を提供するために、ATL によって提供される派生クラスに依存しています。 初期化では、そのクラスによって提供される機能を使用する必要があります (これは、クラスのオブジェクトが他のオブジェクトを集計する必要がある場合は確かに当てはまりますが、クラスのコンストラクターにはこれらの機能にアクセスする方法がないためです)。 クラスの構築コードは、最派生クラスが完全に構築される前に実行されます。

   ただし、 `FinalConstruct`は、ほとんどの派生クラスが完全に構築された直後に呼び出されます。これにより、仮想関数を呼び出し、ATL によって提供される参照カウントの実装を使用できるようになります。

### <a name="example"></a>例

通常は、から`CComObjectRootEx`派生したクラスでこのメソッドをオーバーライドして、集計されたオブジェクトを作成します。 例:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

構築に失敗した場合は、エラーを返すことができます。 また、作成時に内部集計オブジェクトが参照カウントをインクリメントし、カウントを0にデクリメントする場合、マクロ[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)を使用して外部オブジェクトを削除から保護することもできます。

次に、集計を作成する一般的な方法を示します。

- クラスオブジェクトへのポインターを追加し、コンストラクターでNULLに初期化します。`IUnknown`

- を`FinalConstruct`オーバーライドして、集計を作成します。

- [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) マクロのパラメーターとして定義したポインターを使用し`IUnknown`ます。

- を`FinalRelease`オーバーライドして`IUnknown` 、ポインターを解放します。

##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease

派生クラスでこのメソッドをオーバーライドすると、オブジェクトに必要なクリーンアップを実行できます。

```
void FinalRelease();
```

### <a name="remarks"></a>Remarks

既定では`CComObjectRootEx::FinalRelease` 、は何も行いません。

で`FinalRelease`クリーンアップを実行することは、 `FinalRelease`が呼び出された時点でオブジェクトが完全に構築されているため、クラスのデストラクターにコードを追加することをお勧めします。 これにより、最も派生したクラスによって提供されるメソッドに安全にアクセスできます。 これは、削除前に集計されたオブジェクトを解放する場合に特に重要です。

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

非集計オブジェクトの参照カウントを1だけインクリメントします。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>戻り値

診断とテストに役立つ可能性のある値。

### <a name="remarks"></a>Remarks

スレッドモデルがマルチスレッドの場合`InterlockedIncrement` 、を使用して、複数のスレッドが同時に参照カウントを変更できないようにします。

##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface

要求されたインターフェイスへのポインターを取得します。

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*pThis*<br/>
からに`QueryInterface`公開されているインターフェイスの COM マップを格納しているオブジェクトへのポインター。

*pEntries*<br/>
から使用可能なインターフェイス`_ATL_INTMAP_ENTRY`のマップにアクセスする構造体へのポインター。

*iid*<br/>
から要求されているインターフェイスの GUID。

*ppvObject*<br/>
入出力*Iid*で指定されたインターフェイスポインターへのポインター。インターフェイスが見つからない場合は NULL。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

`InternalQueryInterface` が処理するのは、COM マップ テーブル内のインターフェイスのみです。 オブジェクトが集計されて`InternalQueryInterface`いる場合、は外側の不明なに委任しません。 COM マップテーブルには、マクロ[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 、またはそのバリアントの1つを使用して、インターフェイスを入力できます。

##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease

非集計オブジェクトの参照カウントを1だけデクリメントします。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>戻り値

非デバッグビルドとデバッグビルドの両方で、この関数は、診断またはテストに役立つ可能性がある値を返します。 返される正確な値は、使用されるオペレーティングシステムなどの多くの要因によって異なります。また、参照カウントである可能性もあります。

### <a name="remarks"></a>Remarks

スレッドモデルがマルチスレッドの場合`InterlockedDecrement` 、を使用して、複数のスレッドが同時に参照カウントを変更できないようにします。

##  <a name="lock"></a>  CComObjectRootEx::Lock

スレッドモデルがマルチスレッドの場合、このメソッドは Win32 API 関数[EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)を呼び出します。この関数は、スレッドがプライベートデータメンバーを通じて取得したクリティカルセクションオブジェクトの所有権を取得するまで待機します。

```
void Lock();
```

### <a name="remarks"></a>Remarks

保護されたコードの実行が完了したら`Unlock` 、スレッドはを呼び出して、クリティカルセクションの所有権を解放する必要があります。

スレッドモデルがシングルスレッドの場合、このメソッドは何も行いません。

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

4バイトのメモリにアクセスする共用体の一部。

```
long m_dwRef;
```

### <a name="remarks"></a>Remarks

で`m_pOuterUnknown`は、共用体の一部を使用します。

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

オブジェクトが集計されていない場合、および`AddRef` `Release`によってアクセスさ`m_dwRef`れる参照カウントはに格納されます。 オブジェクトが集計されている場合、外側の unknown へのポインターは[m_pOuterUnknown](#m_pouterunknown)に格納されます。

##  <a name="m_pouterunknown"></a>CComObjectRootEx:: m_pOuterUnknown

4バイトのメモリにアクセスする共用体の一部。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Remarks

で`m_dwRef`は、共用体の一部を使用します。

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

オブジェクトが集計されている場合は、外側の不明への`m_pOuterUnknown`ポインターがに格納されます。 オブジェクトが集計されていない場合、および`AddRef` `Release`によってアクセスされる参照カウントは[m_dwRef](#m_dwref)に格納されます。

##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain

オブジェクトマップに示されている各クラスに対して、この関数は、モジュールが初期化されたときに1回、または終了したときに呼び出されます。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>パラメーター

*bStarting*<br/>
入出力クラスが初期化されている場合、値は TRUE になります。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

*Bstarting*パラメーターの値は、モジュールが初期化されているか、終了しているかを示します。 の既定の`ObjectMain`実装では何も実行されませんが、クラスでこの関数をオーバーライドして、クラスに割り当てたいリソースを初期化またはクリーンアップできます。 クラスの`ObjectMain`インスタンスが要求される前に、が呼び出されることに注意してください。

`ObjectMain`は DLL のエントリポイントから呼び出されるため、エントリポイント関数が実行できる操作の種類は制限されます。 これらの制限の詳細については、「 [dll および Visual C++ランタイムライブラリの動作](../../build/run-time-library-behavior.md)と[DllMain](/windows/win32/Dlls/dllmain)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

集計の外側の不明の参照カウントをインクリメントします。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>戻り値

診断とテストに役立つ可能性のある値。

##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface

要求されたインターフェイスへの間接ポインターを取得します。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
から要求されているインターフェイスの GUID。

*ppvObject*<br/>
入出力*Iid*で指定されたインターフェイスポインターへのポインター。または、集計でインターフェイスがサポートされていない場合は NULL。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease

集計の外側の不明部分の参照カウントをデクリメントします。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>戻り値

非デバッグビルドでは、は常に0を返します。 デバッグビルドでは、診断またはテストに役立つ値が返されます。

##  <a name="unlock"></a>CComObjectRootEx:: Unlock

スレッドモデルがマルチスレッドの場合、このメソッドは Win32 API 関数[LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)を呼び出します。これにより、プライベートデータメンバーを通じて取得されたクリティカルセクションオブジェクトの所有権が解放されます。

```
void Unlock();
```

### <a name="remarks"></a>Remarks

所有権を取得するには、 `Lock`スレッドがを呼び出す必要があります。 へ`Lock`の各呼び出しでは、クリティカル`Unlock`セクションの所有権を解放するために、対応する呼び出しが必要です。

スレッドモデルがシングルスレッドの場合、このメソッドは何も行いません。

## <a name="see-also"></a>関連項目

[CComAggObject クラス](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject クラス](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject クラス](../../atl/reference/ccompolyobject-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
