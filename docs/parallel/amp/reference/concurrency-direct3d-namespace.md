---
title: Concurrency::direct3d 名前空間
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: e1374acbd7061afaba372100cf6e69d9d717da8a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127034"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 名前空間

`direct3d` 名前空間は、D3D の相互運用性をサポートする関数を提供します。 AMP コードでの計算に D3D リソースを使用できます。 また、冗長な中間コピーを作成せずに、AMP で作成されたリソースを D3D コードで使用することもできます。 Amp を使用C++して、DirectX アプリケーションの多くのコンピューティング処理を要するセクションを段階的に高速化し、amp 計算から生成されたデータに対して D3D API を使用することができます。

## <a name="syntax"></a>構文

```cpp
namespace direct3d;
```

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|Name|説明|
|----------|-----------------|
|[scoped_d3d_access_lock クラス](scoped-d3d-access-lock-class.md)|`accelerator_view` オブジェクトの D3D アクセスのロックの RAII ラッパー。|

### <a name="structures"></a>構造体

|Name|説明|
|----------|-----------------|
|[adopt_d3d_access_lock_t 構造体](adopt-d3d-access-lock-t-structure.md)|D3D のアクセスのロックを示すタグの種類は、取得するのではなく、導入する必要があります。|

### <a name="functions"></a>関数

|Name|説明|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|引数の絶対値を返します。|
|[クリップ](concurrency-direct3d-namespace-functions-amp.md#clamp)|オーバーロードされます。 _X を指定された _Min と _Max の範囲にクランプします。|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|_X 内で設定されているビットの数をカウントします。|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Direct3D デバイスインターフェイスへのポインターから[Accelerator_view クラス](accelerator-view-class.md)を作成します。|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|と共有されているリソースに対して D3D 操作を安全に実行するために、accelerator_view のロックを取得し accelerator_view|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|ブロックせずに、accelerator_view に対する D3D アクセスのロックを取得します。|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|指定された accelerator_view に対する D3D アクセスのロックを解除します。|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|最上位ビットから下位に向かって操作して、_X 内で最初に設定されているビットの位置を取得します。|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|最下位ビットから上位に向かって操作して、_X 内で最初に設定されているビットの位置を取得します。|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|配列を基にする D3D バッファー インターフェイスを取得します。|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|2つの値を比較し、より大きい値を返します。|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|2つの値を比較して、小さい方の値を返します。|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|指定された accelerator_view についてタイムアウトが無効であるかどうかを示すブール型のフラグを返します。|
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|オーバーロードされます。 3つの引数に対して算術乗算/加算演算を実行します。 _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|D3D バッファーのインターフェイス ポインターから配列を作成します。|
|[聞こえる](concurrency-direct3d-namespace-functions-amp.md#noise)|パーリン ノイズ アルゴリズムを使用して乱数値を生成します。|
|[単位](concurrency-direct3d-namespace-functions-amp.md#radians)|_X を角度からラジアンに変換します。|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|引数の高速近似逆数を計算します。|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|_X 内のビットの順序を反転させます。|
|[彩度](concurrency-direct3d-namespace-functions-amp.md#saturate)|0 ～ 1 の範囲内で _X をクランプします。|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|オーバーロードされます。 引数の正弦を返します。|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|_X が [_Min, _Max] の範囲内にある場合、0 ～ 1 の滑らかなエルミート補間を返します。|
|[画面](concurrency-direct3d-namespace-functions-amp.md#step)|2 つの値を比較し、どちらの値が大きいかに応じて 0 または 1 を返します。|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|2つの符号なしの値を比較し、より大きい値を返します。|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|2つの符号なしの値を比較し、小さい方の値を返します。|

## <a name="requirements"></a>要件

**ヘッダー:** amp.h

**名前空間:** Concurrency

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
