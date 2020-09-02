---
title: IDebugExceptionEvent2::P Асстодебугжее | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecc7eb3830522cdee0022f4193482daab3780230
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150400"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, должно ли исключение передаваться в отлаживаемую программу при возобновлении выполнения или если исключение должно быть отклонено.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fPass`  
 окне Ненулевое значение ( `TRUE` ), если исключение должно быть передано в программу, отлаживаемой при возобновлении выполнения, или нуль ( `FALSE` ), если исключение должно быть отклонено.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Вызов этого метода фактически не приводит к выполнению кода в отлаживаемой программе. Вызов просто устанавливает состояние для следующего выполнения кода. Например, вызовы метода [канпасстодебугжее](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) могут возвращать `S_OK` [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` для поля задано значение `EXCEPTION_STOP_SECOND_CHANCE` .  
  
 Интегрированная среда разработки может получить событие [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) и вызвать метод [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . Обработчик отладки (DE) должен иметь поведение по умолчанию для обработки ситуации, если `PassToDebuggee` метод не вызывается.  
  
## <a name="see-also"></a>См. также:  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [канпасстодебугжее](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
