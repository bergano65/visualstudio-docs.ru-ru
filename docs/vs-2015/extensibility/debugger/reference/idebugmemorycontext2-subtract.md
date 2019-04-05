---
title: IDebugMemoryContext2::Subtract | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2efe4e15c5489ef07741a0d267b9c1b870d07aa8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989535"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Вычитает указанное значение из текущего контекста и возвращает новый контекст.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Число байтов памяти, чтобы уменьшить.  
  
 `ppMemCxt`  
 [out] Возвращает новый [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Контекст памяти — это адрес, поэтому значение вычитается из адреса создает новый адрес, который требуется новый интерфейс контекста.  
  
 Этот метод всегда должен создавать новый контекст, даже если Итоговый адрес находится вне области памяти, связанный с данным контекстом. Единственное исключение — если недостаточно памяти, выделяемой для нового контекста или `ppMemCxt` имеет нулевое значение (который является ошибкой).  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
