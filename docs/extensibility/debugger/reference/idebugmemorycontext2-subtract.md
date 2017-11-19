---
title: "IDebugMemoryContext2::Subtract | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b1dc686846e0ca1e60f6bfce03dc5976c0d1d34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Вычитает указанное значение в текущем контексте и возвращает новый контекст.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCount`  
 [in] Число байтов памяти, для уменьшения.  
  
 `ppMemCxt`  
 [out] Возвращает новый [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Контекст памяти — это адрес, поэтому полученное значение вычитается из адреса создает новый адрес, который требуется новый интерфейс контекста.  
  
 Этот метод всегда должен создавать новый контекст, даже если Итоговый адрес находится вне области памяти, связанный с данным контекстом. Единственное исключение — если памяти не может быть выделено для нового контекста или `ppMemCxt` имеет значение null (который является ошибкой).  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)