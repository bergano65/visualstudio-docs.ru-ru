---
title: "IDebugProperty3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3"
helpviewer_keywords: 
  - "Интерфейс IDebugProperty3"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс обеспечивает поддержку:  
  
-   Извлечение произвольно длинная строка, связанная со свойством.  
  
-   Связывание уникальный идентификатор со свойством.  
  
-   Получить список пользовательских средств просмотра для свойства.  
  
-   Устанавливать значение свойства с возможностью сообщить все результирующие ошибки  
  
## Синтаксис  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс на одном и том же объекта, реализующего IDebugProperty2, чтобы обеспечить поддержку длинных строк, идентификаторы свойств и пользовательских средств просмотра.  
  
## Замечания для вызывающих объектов  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugProperty2` интерфейс для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 В дополнение к методам, наследуемым от интерфейса `IDebugProperty2`, интерфейс `IDebugProperty3` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Возвращает длину строки, связанной со свойством.|  
|[GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)|Возвращает строку в пользователь\-поставленном буфере.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Создает уникальный идентификатор для данного свойства.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Уничтожает уникальный идентификатор для данного свойства.|  
|[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)|Возвращает количество пользовательских средств просмотра, что это свойство можно просмотреть с помощью.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Возвращает список пользовательских средств просмотра, что это свойство можно просмотреть с помощью.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Устанавливает значение данного свойства, возвращается сообщение об ошибке, если что\-либо пошло неправильно.|  
  
## Заметки  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) предпочтительным способом для сеанса отладки \(SDM\) диспетчер для задания значения этого свойства.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)