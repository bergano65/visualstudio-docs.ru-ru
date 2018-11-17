---
title: IDebugStackFrame2::GetPhysicalStackRange | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40aab7702f4e7c50a0aa699b0f623aa107d4e9cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761928"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает представление зависит от компьютера диапазона физических адресов, связанных с кадром стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `paddrMin`  
 [out] Возвращает наименьший физический адрес, связанный с данным кадром стека.  
  
 `paddrMax`  
 [out] Возвращает наибольший физический адрес, связанный с данным кадром стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые этим методом используется диспетчер отладки сеансов (SDM) для сортировки кадров стека.  
  
 Предполагается, что стек вызовов растет вниз, то есть, что с более низким адресами памяти добавляются новые кадры стека. Архитектура среды выполнения необходимо указать физический стек диапазоны, которые соответствуют это предположение.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

