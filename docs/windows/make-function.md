---
title: "Make 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Make"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Make 関数"
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Make 関数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] の指定クラスを初期化します。  同じモジュールで定義されたコンポーネントをインスタンス化するには、この関数を使用します。  
  
## 構文  
  
```  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8,  
   typename TArg9  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8,  
   TArg9 &&arg9  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2  
);  
template <  
   typename T,  
   typename TArg1  
>  
ComPtr<T> Make(  
   TArg1 &&arg1  
);  
template <  
   typename T  
>  
ComPtr<T> Make();  
```  
  
#### パラメーター  
 `T`  
 `WRL::RuntimeClass`から継承するユーザーが指定するクラス。  
  
 `TArg1`  
 指定したランタイム クラスに渡される引数 1 の型。  
  
 `TArg2`  
 指定したランタイム クラスに渡される引数 2 の型。  
  
 `TArg3`  
 指定したランタイム クラスに渡される引数 3 の型。  
  
 `TArg4`  
 指定したランタイム クラスに渡される引数 4 の型。  
  
 `TArg5`  
 指定したランタイム クラスに渡される引数 5 の型。  
  
 `TArg6`  
 指定したランタイム クラスに渡される引数 6 の型。  
  
 `TArg7`  
 指定したランタイム クラスに渡される引数 7 の型。  
  
 `TArg8`  
 指定したランタイム クラスに渡される引数 8 の型。  
  
 `TArg9`  
 指定したランタイム クラスに渡される引数 9 の型。  
  
 `arg1`  
 指定したランタイム クラスに渡される引数 1。  
  
 `arg2`  
 指定したランタイム クラスに渡される引数 2。  
  
 `arg3`  
 指定したランタイム クラスに渡される引数 3。  
  
 `arg4`  
 指定したランタイム クラスに渡される引数 4。  
  
 `arg5`  
 指定したランタイム クラスに渡される引数 5。  
  
 `arg6`  
 指定したランタイム クラスに渡される引数 6。  
  
 `arg7`  
 指定したランタイム クラスに渡される引数 7。  
  
 `arg8`  
 指定したランタイム クラスに渡される引数 8。  
  
 `arg9`  
 指定したランタイム クラスに渡される引数 9。  
  
## 戻り値  
 正常終了した場合 `ComPtr<T>` オブジェクト; それ以外の場合は `nullptr`。  
  
## 解説  
 この関数で [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)間で、この例の違いについては [方法: WRL コンポーネントを直接インスタンス化する](../windows/how-to-instantiate-wrl-components-directly.md) を参照してください。  
  
## 必要条件  
 **ヘッダー:** implements.h  
  
 **名前空間:** Microsoft::WRL  
  
## 参照  
 [Microsoft::WRL 名前空間](../windows/microsoft-wrl-namespace.md)