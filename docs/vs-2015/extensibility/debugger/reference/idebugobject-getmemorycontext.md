---
title: IDebugObject::GetMemoryContext | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20f4704ad8fa1cb16974d73803e1c5f49da9f71b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559657"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugObject::GetMemoryContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-getmemorycontext).  
  
Получает контекст памяти, представляющий адрес значения объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pContext`  
 [out] Возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект, представляющий адрес значения объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Контекст возвращаемый памяти указывает адрес значения, представленных в данном [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекта.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

