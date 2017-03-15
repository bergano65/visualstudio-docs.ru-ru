---
title: "IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFormalTypeParams"
  - "IDebugGenericFieldDefinition::GetFormalTypeParams"
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает параметры типа, учитывая количество параметров.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```c#  
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
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Заметки  
 Возвращает параметры типа в порядке слева направо. Например Dictionary \< K, V > Возвращает IDebugFormalGenericParameters {K, V}.  
  
## <a name="see-also"></a>См. также  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)