---
title: IDebugGenericFieldInstance::GetTypeArguments | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 09c9f4c9a6c54e3283945a4a20fda81b560fe0a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568911"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugGenericFieldInstance::GetTypeArguments](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments).  
  
Получает аргументы параметра типа для данного экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetTypeArguments(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   ULONG32*      pcArgs  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint              cArgs,  
   out IDebugField[] ppArgs,  
   ref uint          pcArgs  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cArgs`  
 [in] Число параметров типа.  
  
 `ppArgs`  
 [out] Возвращает массив параметров типа.  
  
 `pcArgs`  
 [in, out] Число элементов в `ppArgs` массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)

