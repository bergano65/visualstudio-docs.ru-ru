---
title: "Функция SccCloseProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCloseProject"
helpviewer_keywords: 
  - "Функция SccCloseProject"
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Функция SccCloseProject
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция закрывает проект, отмечающую конец определенного сеанса.  
  
## Синтаксис  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### Параметры  
 pvContext  
 Структура подключаемого модуля контекста исходного элемента управления.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Проект успешно закрыт.|  
|SCC\_E\_PROJNOTOPEN|Проект не открыт.|  
|SCC\_E\_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC\_E\_NONSPECIFICERROR|Неспецифическая ошибка.|  
  
## Заметки  
 [SccOpenProject](../extensibility/sccopenproject-function.md) Всегда вызывается перед этой функции. Вызов этой функции выполняется путем вызова либо `SccOpenProject` функции или [SccUninitialize](../extensibility/sccuninitialize-function.md), который полностью завершает подключение к системе управления версиями.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)