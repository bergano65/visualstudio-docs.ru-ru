---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Выполняет программу отладчика.  Поток возвращается для предоставления сведений отладчика, на которых поток пользователь просматривает выполнение программы.  
  
## Синтаксис  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### Параметры  
 `pThread`  
 \[in\] IDebugThread2 объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 3 Различными способами, что отладчик может возобновить выполнение после остановки.  
  
-   Выполните: Не смогут отменять любой предыдущий шаг, и запускается до следующей точки останова и т д  
  
-   Шаг: Отмена любой старый шаг и запуск нового шага до завершения.  
  
-   Продолжайте: Запустите снова и оставить старый активный любого этапа.  
  
 Поток, передаваемый `ExecuteOnThread` удобно использовать при решении того, авторизирован, шаг, который требуется отменить.  Если неизвестно, то при выполнении потока выполнения отменяет все шаги.  С набором знаний потока, нужно только отмены шага на активном потоке.  
  
## См. также  
 [Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)