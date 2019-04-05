---
title: IDebugExceptionEvent2::CanPassToDebuggee | Документация Майкрософт
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993922"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет, поддерживает ли модуль отладки (DE) можно передать это исключение для отлаживаемой при возобновлении выполнения программы.  
  
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
 Возвращает один `S_OK` (исключение может передаваться в программу) или `S_FALSE` (исключение не может быть передано в).  
  
## <a name="remarks"></a>Примечания  
 DE должен иметь действие по умолчанию для передачи для отлаживаемой программы. Интегрированная среда разработки может появиться [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событий и вызовов [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md) метод без вызова `CanPassToDebuggee` метод. Таким образом DE должны иметь варианта по умолчанию для передачи в исключение, или нет.  
  
## <a name="see-also"></a>См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
