---
title: IDebugProgram2::Execute | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19cb88a24a616a2a39bdcd7f292108493859a8b7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919048"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Продолжает выполнение программы в остановленном состоянии. Очистить все предыдущие состояния выполнения (например, шаг), и начнется снова выполнение программы.  
  
> [!NOTE]
>  Этот метод является нерекомендуемым. Используйте [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) метод вместо этого.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда пользователь начинает выполнение в остановленном состоянии в поток некоторые другие программы, этот метод вызывается для данной программы. Этот метод также вызывается, когда пользователь выбирает **запустить** команду **Отладка** меню в интегрированной среде разработки. Реализация этого метода может быть простым вызовом [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) метода в текущем потоке в программе.  
  
> [!WARNING]
>  В случае остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)