---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
Вынуждает текущий поток отключения и отправляет уведомление точки останова в интегрированной среде разработки отладчика.  
  
## Синтаксис  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### Параметры  
 `br`  
 \[in\] причина прерывания.  
  
 `pbra`  
 \[out\] действие, выполняемое при возобновлении приложения отладчик.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Обработчик языка вызывает этот метод в контексте потока, который ударяет точку останова.  Этот метод блокирует текущий поток и отправляет уведомление точки останова в интегрированной среде разработки отладчика.  Когда отладчик, откуда приложение параметр `pbra` указывает, какое действие.  
  
> [!NOTE]
>  Обработчик языка может быть вызван потоком для выполнения задач, как перечисляет кадры стека или вычисляет выражения в процессе точки останова.  
  
 Этот метод вызывает `IApplicationDebugger::onHandleBreakPoint` непосредственного вызова.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)