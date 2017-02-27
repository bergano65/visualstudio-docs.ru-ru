---
title: "IDebugTypeFieldBuilder::CreatePrimitive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreatePrimitive"
  - "IDebugTypeFieldBuilder::CreatePrimitive"
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugTypeFieldBuilder::CreatePrimitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает объект, который представляет тип-примитив.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CreatePrimitive (  
   DWORD          dwElementType,  
   IDebugField ** pTypeField  
);  
```  
  
```c#  
int CreatePrimitive (  
   uint            dwElementType,  
   out IDebugField pTypeField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwElementType`  
 [in] Значение из [перечисление CorElementType](CorElementType%20Enumeration.xml) представляющий тип-примитив.  
  
 `pTypeField`  
 [out] Возвращает интерфейс IDebugField для нового типа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)