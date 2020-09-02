---
title: 'IDebugProcess2:: EnumThreads | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e9b6447827baa80da2843c992a8d2233dd1a4b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188021"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает список всех потоков, выполняющихся в процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 заполняет Возвращает объект [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) , содержащий список всех потоков во всех программах в процессе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод перечисляет потоки, выполняемые в каждой программе, а затем объединяет их в представление процесса потоков. Один поток может выполняться в нескольких программах; Этот метод перечисляет этот поток только один раз.  
  
 Этот метод представляет список потоков процесса без дубликатов. В противном случае для перечисления потоков, выполняющихся в определенной программе, используйте метод [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
