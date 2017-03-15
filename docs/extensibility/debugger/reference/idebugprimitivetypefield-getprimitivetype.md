---
title: "IDebugPrimitiveTypeField::GetPrimitiveType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetPrimitiveType"
  - "IDebugPrimitiveTypeField::GetPrimitiveType"
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPrimitiveTypeField::GetPrimitiveType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает тип-примитив, связанный с этим полем.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPrimitiveType (  
   DWORD* pdwType  
);  
```  
  
```c#  
int GetPrimitiveType (  
   out uint pdwType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwType`  
 [out] Значение из [перечисление CorElementType](CorElementType%20Enumeration.xml) представляющий тип-примитив.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае — возвращает `S_FALSE`.  
  
## <a name="see-also"></a>См. также  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)