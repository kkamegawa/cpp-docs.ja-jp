---
title: '方法: 作成し、CComPtr および CComQIPtr インスタンスを使用'
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 2bcabfe80185939b899c84fc44f71b98608fc3c7
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220550"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>方法: 作成し、CComPtr および CComQIPtr インスタンスを使用

従来の Windows プログラミングでは、ライブラリは、多くの場合、COM オブジェクトとして (厳密には COM サーバーとして) 実装されます。 多くの Windows オペレーティング システム コンポーネントは COM サーバーとして実装されており、多くの共同作成者からこの形式のライブラリが提供されています。 COM の詳細については、「 [Component Object Model (COM)](/windows/desktop/com/component-object-model--com--portal)」を参照してください。

コンポーネント オブジェクト モデル (COM) オブジェクトをインスタンス化するときは、デストラクターの `AddRef` と `Release` の呼び出しを使用して参照のカウントを実行する COM スマート ポインターにインターフェイス ポインターを格納します。 Active Template Library (ATL) または Microsoft Foundation Class ライブラリ (MFC) を使用している場合は、 `CComPtr` スマート ポインターを使用します。 ATL または MFC を使用していない場合は、 `_com_ptr_t`を使用します。 COM には `std::unique_ptr`に相当するものがないため、これらのスマート ポインターを単一所有者のシナリオと複数所有者のシナリオの両方に使用します。 `CComPtr` と `ComQIPtr` のどちらも、右辺値参照が含まれる移動操作をサポートしています。

## <a name="example"></a>例

次の例は、 `CComPtr` を使用して COM オブジェクトをインスタンス化し、そのインターフェイスへのポインターを取得する方法を示しています。 COM オブジェクトを作成するために `CComPtr::CoCreateInstance` メンバー関数が使用されている点に注意してください (同じ名前を持つ Win32 関数ではありません)。

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` その関連は、ATL の一部であるありで定義された\<atlcomcli.h >。 `_com_ptr_t` 宣言されている\<comip.h >。 コンパイラは、タイプ ライブラリのラッパー クラスを生成するときに `_com_ptr_t` の特殊化を作成します。

## <a name="example"></a>例

ATL では、よりシンプルな構文を持つ `CComQIPtr`も提供されます。これを使用して COM オブジェクトに対するクエリを実行して、追加のインターフェイスを取得できます。 ただし、 `CComPtr` で実行できることのすべてを実行可能であるうえ、未加工の COM インターフェイス ポインターとセマンティクス的により整合性の高い `CComQIPtr` をお勧めします。 `CComPtr` を使用してインターフェイスを照会すると、新しいインターフェイス ポインターが出力パラメーターに配置されます。 呼び出しが失敗した場合、HRESULT が返されます。これは、COM の一般的なパターンです。 `CComQIPtr`の場合、戻り値はポインター自体です。呼び出しが失敗した場合、内部 HRESULT 戻り値にはアクセスできません。 次の 2 つの行から、 `CComPtr` と `CComQIPtr` におけるエラー処理機構の違いがわかります。

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>例

`CComPtr` では、IDispatch の特殊化を提供して、COM オートメーション コンポーネントへのポインターを格納し、遅延バインディングを使用してインターフェイスのメソッドを呼び出すことができるようにしています。 `CComDispatchDriver` は `CComQIPtr<IDispatch, &IIDIDispatch>`の typedef であり、 `CComPtr<IDispatch>`に暗黙的に変換可能です。 したがって、これらの 3 つの名前のいずれかがコードに使用されている場合、そのコードは `CComPtr<IDispatch>`と同じです。 次の例に、 `CComPtr<IDispatch>`を使用して Microsoft Word オブジェクト モデルへのポインターを取得する方法を示します。

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>関連項目

[スマート ポインター (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
