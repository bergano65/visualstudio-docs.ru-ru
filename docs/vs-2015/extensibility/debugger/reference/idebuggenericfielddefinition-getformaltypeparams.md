---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Документация Майкрософт
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
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3eb40b1b24ca70e0ce1f44490c80231827b5fe1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558322"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugGenericFieldDefinition::GetFormalTypeParams](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams).  
  
Получает параметры типа, учитывая количество параметров.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```csharp  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cParams`  
 [in] Число параметров.  
  
 `ppParams`  
 [out] Массив параметров типа.  
  
 `pcParams`  
 [in, out] Число параметров в `ppParams` массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Возвращает параметры типа в порядке слева направо. Например, словарь\<K, V > Возвращает IDebugFormalGenericParameters {K, V}.  
  
## <a name="see-also"></a>См. также  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

