---
title: "出たリソース クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: bb4bbd110552d1e3cf604add44de7e428d2703ee
ms.lasthandoff: 02/24/2017

---
# <a name="cautovectorptr-class"></a>出たリソース クラス
このクラスは、新しいベクトルを使用してスマート ポインター オブジェクトを表し、オペレーターを削除します。  
  
> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。  
  
## <a name="syntax"></a>構文  
  
```
template<typename T>  
class CAutoVectorPtr
```  
  
#### <a name="parameters"></a>パラメーター  
 `T`  
 ポインター型。  
  
## <a name="members"></a>メンバー  
  
### <a name="public-constructors"></a>パブリック コンストラクター  
  
|名前|説明|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|コンストラクターです。|  
|[出たリソース:: ~ 出たリソース](#dtor)|デストラクターです。|  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|指すオブジェクトの配列に必要なメモリを割り当てるには、このメソッドを呼び出す`CAutoVectorPtr`します。|  
|[CAutoVectorPtr::Attach](#attach)|既存のポインターの所有権を取得するには、このメソッドを呼び出します。|  
|[CAutoVectorPtr::Detach](#detach)|ポインターの所有権を解放するには、このメソッドを呼び出します。|  
|[CAutoVectorPtr::Free](#free)|指すオブジェクトを削除するには、このメソッドを呼び出して、`CAutoVectorPtr`です。|  
  
### <a name="public-operators"></a>パブリック演算子  
  
|名前|説明|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|キャスト演算子です。|  
|[CAutoVectorPtr::operator =](#operator_eq)|代入演算子です。|  
  
### <a name="public-data-members"></a>パブリック データ メンバー  
  
|名前|説明|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|ポインターのデータ メンバー変数です。|  
  
## <a name="remarks"></a>コメント  
 このクラスは、作成およびスコープ外にあるときに自動的にリソースを解放して、メモリ リークを防ぐため、スマート ポインターを管理するためのメソッドを提供します。 `CAutoVectorPtr`ような`CAutoPtr`、されていることが唯一の違い`CAutoVectorPtr`を使用して[new[] をベクトル](../../standard-library/new-operators.md#operator_new_arr)と[ベクトル delete](../../standard-library/new-operators.md#operator_delete_arr) 、C++ ではなくメモリ割り当てし、解放を**新しい**と**削除**演算子。 参照してください[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)場合のコレクション クラス`CAutoVectorPtr`が必要です。  

  
 参照してください[CAutoPtr](../../atl/reference/cautoptr-class.md)たとえばのスマート ポインター クラスを使用します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** atlbase.h  
  
##  <a name="allocate"></a>CAutoVectorPtr::Allocate  
 指すオブジェクトの配列に必要なメモリを割り当てるには、このメソッドを呼び出す`CAutoVectorPtr`します。  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>パラメーター  
 `nElements`  
 配列の要素数。  
  
### <a name="return-value"></a>戻り値  
 失敗した場合に、メモリが正常にある場合は true を返しますが割り当てられます。  
  
### <a name="remarks"></a>コメント  
 デバッグ ビルドで、アサーション エラーが発生場合、 [CAutoVectorPtr::m_p](#m_p)メンバー変数は、現在は、既存の値を指します。 つまり、null はありません。  
  
##  <a name="attach"></a>CAutoVectorPtr::Attach  
 既存のポインターの所有権を取得するには、このメソッドを呼び出します。  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>パラメーター  
 `p`  
 `CAutoVectorPtr` This ポインターの所有権を持つオブジェクト。  
  
### <a name="remarks"></a>コメント  
 ときに、`CAutoVectorPtr`オブジェクトへのポインターの所有権を取得するに自動的に削除されますポインターと、割り当てられているデータ スコープ外になったときにします。 場合[CAutoVectorPtr::Detach](#detach)が呼び出されると、プログラマ再度責任を解放するいずれかの指定されたリソースが割り当てられます。  
  
 デバッグ ビルドで、アサーション エラーが発生場合、 [CAutoVectorPtr::m_p](#m_p)メンバー変数は、現在は、既存の値を指します。 つまり、null はありません。  
  
##  <a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
 コンストラクターです。  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>パラメーター  
 `p`  
 既存のポインター。  
  
### <a name="remarks"></a>コメント  
 `CAutoVectorPtr`オブジェクトの作成は、既存のポインターを使用して、このような場合、ポインターの所有権を転送します。  
  
##  <a name="dtor"></a>出たリソース:: ~ 出たリソース  
 デストラクターです。  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>コメント  
 割り当てられたリソースを解放します。 呼び出し[CAutoVectorPtr::Free](#free)します。  
  
##  <a name="detach"></a>CAutoVectorPtr::Detach  
 ポインターの所有権を解放するには、このメソッドを呼び出します。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>戻り値  
 ポインターのコピーを返します。  
  
### <a name="remarks"></a>コメント  
 ポインターの所有権を解放、 [CAutoVectorPtr::m_p](#m_p)メンバー変数を NULL にし、ポインターのコピーを返します。 呼び出した後**デタッチ**が解放はプログラマの責任割り当て済みリソースを`CAutoVectorPtr`オブジェクトがある以前責任を負っています。  
  
##  <a name="free"></a>CAutoVectorPtr::Free  
 指すオブジェクトを削除するには、このメソッドを呼び出して、`CAutoVectorPtr`です。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>コメント  
 によって指されるオブジェクト、`CAutoVectorPtr`が解放されると、 [CAutoVectorPtr::m_p](#m_p)メンバー変数が NULL に設定します。  
  
##  <a name="m_p"></a>CAutoVectorPtr::m_p  
 ポインターのデータ メンバー変数です。  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>コメント  
 このメンバー変数は、ポインターの情報を保持します。  
  
##  <a name="operator_eq"></a>CAutoVectorPtr::operator =  
 代入演算子です。  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>パラメーター  
 `p`  
 ポインター。  
  
### <a name="return-value"></a>戻り値  
 参照を返す、**出たリソース\<T >**します。  
  
### <a name="remarks"></a>コメント  
 代入演算子をデタッチ、`CAutoVectorPtr`オブジェクトを現在のポインターから新しいポインターのアタッチと`p`、その場所にします。  
  
##  <a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 キャスト演算子です。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>コメント  
 クラス テンプレートで定義されたオブジェクト データ型へのポインターを返します。  
  
## <a name="see-also"></a>関連項目  
 [CAutoPtr クラス](../../atl/reference/cautoptr-class.md)   
 [クラスの概要](../../atl/atl-class-overview.md)
