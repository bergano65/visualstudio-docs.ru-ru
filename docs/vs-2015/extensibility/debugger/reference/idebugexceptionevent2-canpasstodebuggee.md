---
title: 'IDebugExceptionEvent2:: Канпасстодебугжее | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 383287a027a75adfb4c58020675e08a46198eacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163813"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет, поддерживает ли модуль отладки (DE) возможность передачи этого исключения в отлаживаемую программу при возобновлении выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает либо `S_OK` (исключение может быть передано в программу), либо `S_FALSE` (исключение не может быть передано).  
  
## <a name="remarks"></a>Remarks  
 Параметру DE должно быть назначено действие по умолчанию для передачи в отлаживаемый отладчик. Интегрированная среда разработки может получить событие [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) и вызвать метод [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) , не вызывая `CanPassToDebuggee` метод. Таким образом, DE должен иметь вариант по умолчанию для передачи исключения в или нет.  
  
## <a name="see-also"></a>См. также:  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
