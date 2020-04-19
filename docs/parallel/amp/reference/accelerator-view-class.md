---
title: accelerator_view クラス
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 8990566fb3a700d61de324f725dea3ec00006d04
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127177"
---
# <a name="accelerator_view-class"></a>accelerator_view クラス

C ++. AMP のデータ並列アクセラレータでの仮想デバイスの抽象化を表します。

## <a name="syntax"></a>構文

```cpp
class accelerator_view;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[accelerator_view コンストラクター](#ctor)|`accelerator_view` クラスの新しいインスタンスを初期化します。|
|[~ accelerator_view デストラクター](#dtor)|`accelerator_view` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[create_marker](#create_marker)|これまでにこの `accelerator_view` オブジェクトに送信されたすべてのコマンドの完了を追跡するために予定を返します。|
|[flush](#flush)|`accelerator_view` オブジェクトのキューに格納されたすべての保留中のコマンドを実行のためにアクセラレータに送信します。|
|[get_accelerator](#get_accelerator)|`accelerator` オブジェクトの `accelerator_view` オブジェクトを返します。|
|[get_is_auto_selection](#get_is_auto_selection)|`accelerator_view` オブジェクトが[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)に渡されたときに、ランタイムが適切なアクセラレータを自動的に選択するかどうかを示すブール値を返します。|
|[get_is_debug](#get_is_debug)|`accelerator_view` オブジェクトに広範なエラー レポートに有効なデバッグ レイヤーがあるかどうかを示すブール値を返します。|
|[get_queuing_mode](#get_queuing_mode)|`accelerator_view` オブジェクトのキュー モードを返します。|
|[get_version](#get_version)|`accelerator_view` のバージョンを返します。|
|[待機](#wait)|終了する `accelerator_view` オブジェクトに送信されるすべてのコマンドを待機します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[operator!=](#operator_neq)|この `accelerator_view` オブジェクトと別のオブジェクトを比較し、同じである場合は**false**を返します。それ以外の場合は**true**を返します。|
|[operator=](#operator_eq)|指定された `accelerator_view` オブジェクトの内容をこのオブジェクトにコピーします。|
|[operator==](#operator_eq_eq)|この `accelerator_view` オブジェクトと別のオブジェクトを比較し、同じである場合は**true**を返します。それ以外の場合は**false**を返します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[アクセラレーター](#accelerator)|`accelerator` オブジェクトの `accelerator_view` オブジェクトを取得します。|
|[is_auto_selection](#is_auto_selection)|`accelerator_view` オブジェクトが[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)に渡されたときに、ランタイムが適切なアクセラレータを自動的に選択するかどうかを示すブール値を取得します。|
|[is_debug](#is_debug)|`accelerator_view` オブジェクトに広範なエラー レポートに有効なデバッグ レイヤーがあるかどうかを示すブール値を取得します。|
|[queuing_mode](#queuing_mode)|`accelerator_view` オブジェクトのキュー モードを取得します。|
|[version](#version)|accelerator のバージョンを取得します。|

## <a name="inheritance-hierarchy"></a>継承階層

`accelerator_view`

### <a name="remarks"></a>コメント

`accelerator_view` オブジェクトは、アクセラレータの論理的で分離されたビューを表します。 単一の物理計算デバイスは、多くの論理的で分離された `accelerator_view` オブジェクトを使用できます。 各アクセラレータには既定の `accelerator_view` オブジェクトがあります。 追加の `accelerator_view` オブジェクトを作成できます。

物理デバイスは、多くのクライアント スレッド間で共有できます。 クライアント スレッドがアクセラレータの同じ `accelerator_view` オブジェクトを協調的に使用することができるか、または、各クライアントが他のクライアント スレッドから分離するために独立した `accelerator_view` オブジェクトを使用して計算デバイスと通信できます。

`accelerator_view` オブジェクトは、2つの[Queuing_mode 列挙](concurrency-namespace-enums-amp.md#queuing_mode)状態のいずれかを持つことができます。 キュー モードが `immediate` である場合、`copy` および `parallel_for_each` のようなコマンドが呼び出し元に戻るとすぐに対応するアクセラレータ デバイスに送信されます。 キュー モードが `deferred` の場合、このようなコマンドは `accelerator_view` オブジェクトに対応するコマンド キューに置かれます。 コマンドは、`flush()` が呼び出されるまでデバイスに実際に送信されません。

## <a name="requirements"></a>要件

**ヘッダー:** amprt. h

**名前空間:** Concurrency

## <a name="accelerator"></a>アクセラレーター

Accelerator_view オブジェクトのアクセラレータオブジェクトを取得します。

### <a name="syntax"></a>構文

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a>accelerator_view

既存の `accelerator_view` オブジェクトをコピーすることによって、accelerator_view クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>パラメーター

*other*<br/>
コピーする `accelerator_view` オブジェクトです。

## <a name="create_marker"></a>create_marker

これまでにこの `accelerator_view` オブジェクトに送信されたすべてのコマンドの完了を追跡するために予定を返します。

### <a name="syntax"></a>構文

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>戻り値

これまでこの `accelerator_view` オブジェクトに送信されたすべてのコマンドの完了を追跡するための予定です。

## <a name="flush"></a>flush

Accelerator_view オブジェクトにキューに置かれている保留中のすべてのコマンドを、実行のためにアクセラレータに送信します。

### <a name="syntax"></a>構文

```cpp
void flush();
```

### <a name="return-value"></a>戻り値

`void` を返します。

## <a name="get_accelerator"></a>get_accelerator

Accelerator_view オブジェクトのアクセラレータオブジェクトを返します。

### <a name="syntax"></a>構文

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>戻り値

Accelerator_view オブジェクトの accelerator オブジェクト。

## <a name="get_is_auto_selection"></a>get_is_auto_selection

Accelerator_view が[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)に渡されたときに、ランタイムが適切なアクセラレータを自動的に選択するかどうかを示すブール値を返します。

### <a name="syntax"></a>構文

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>戻り値

ランタイムが適切なアクセラレータを自動的に選択する場合は**true** 。それ以外の場合は**false**。

## <a name="get_is_debug"></a>get_is_debug

Accelerator_view オブジェクトの詳細なエラー報告が有効になっているデバッグ層があるかどうかを示すブール値を返します。

### <a name="syntax"></a>構文

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>戻り値

`accelerator_view` オブジェクトの詳細なエラー報告に対してデバッグレイヤーが有効になっているかどうかを示すブール値です。

## <a name="get_queuing_mode"></a>get_queuing_mode

Accelerator_view オブジェクトのキューモードを返します。

### <a name="syntax"></a>構文

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>戻り値

`accelerator_view` オブジェクトのキューモード。

## <a name="get_version"></a>get_version

Accelerator_view のバージョンを返します。

### <a name="syntax"></a>構文

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>戻り値

`accelerator_view` のバージョン。

## <a name="is_auto_selection"></a>is_auto_selection

Accelerator_view が[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)に渡されたときに、ランタイムが適切なアクセラレータを自動的に選択するかどうかを示すブール値を取得します。

### <a name="syntax"></a>構文

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a>is_debug

Accelerator_view オブジェクトの詳細なエラー報告が有効になっているデバッグ層があるかどうかを示すブール値を取得します。

### <a name="syntax"></a>構文

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator_neq"></a>operator! =

この accelerator_view オブジェクトと別のオブジェクトを比較し、同じである場合は**false**を返します。それ以外の場合は**true**を返します。

### <a name="syntax"></a>構文

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>パラメーター

*other*<br/>
このと比較する `accelerator_view` オブジェクト。

### <a name="return-value"></a>戻り値

2つのオブジェクトが同じ場合は**false** 。それ以外の場合は**true**です。

## <a name="operator_eq"></a>operator =

指定された accelerator_view オブジェクトの内容をこのオブジェクトにコピーします。

### <a name="syntax"></a>構文

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>パラメーター

*other*<br/>
コピー元の `accelerator_view` オブジェクト。

### <a name="return-value"></a>戻り値

変更された `accelerator_view` オブジェクトへの参照。

## <a name="operator_eq_eq"></a>operator = =

この accelerator_view オブジェクトと別のオブジェクトを比較し、同じである場合は**true**を返します。それ以外の場合は**false**を返します。

### <a name="syntax"></a>構文

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>パラメーター

*other*<br/>
このと比較する `accelerator_view` オブジェクト。

### <a name="return-value"></a>戻り値

2つのオブジェクトが同じ場合は**true** 。それ以外の場合は**false**。

## <a name="queuing_mode"></a>queuing_mode

Accelerator_view オブジェクトのキューモードを取得します。

### <a name="syntax"></a>構文

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>バージョン

Accelerator_view のバージョンを取得します。

### <a name="syntax"></a>構文

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

Accelerator_view オブジェクトに送信されたすべてのコマンドが終了するまで待機します。

### <a name="syntax"></a>構文

```cpp
void wait();
```

### <a name="return-value"></a>戻り値

`void` を返します。

### <a name="remarks"></a>コメント

[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)が `immediate`の場合、このメソッドは、ブロックなしですぐに制御を戻します。

## <a name="dtor"></a>~ accelerator_view

Accelerator_view オブジェクトを破棄します。

### <a name="syntax"></a>構文

```cpp
~accelerator_view();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
