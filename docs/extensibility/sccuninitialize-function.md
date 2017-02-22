---
title: "Функция SccUninitialize | Microsoft Docs"
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
  - "SccUninitialize"
helpviewer_keywords: 
  - "Функция SccUninitialize"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccUninitialize
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция очищает все распределения или открытых соединений, созданных предыдущим вызовом [SccInitialize](../extensibility/sccinitialize-function.md) в процессе подготовки к выключению подключаемый модуль системы управления версиями.  
  
## Синтаксис  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### Параметры  
 pvContext  
 \[in\] Указатель на структуру источника управления подключаемый модуль контекст создан в [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Очистка завершена успешно.|  
  
## Заметки  
 Подключаемый модуль системы управления версиями отвечает за завершает работу и освобождения памяти, выделенной подключаемый модуль для структуры контекста. Функция вызывается один раз для каждого заданного экземпляра подключаемого модуля. Вызов [SccInitialize](../extensibility/sccinitialize-function.md) предшествует этот вызов. Нет проектов по\-прежнему могут быть открыты во время вызова `SccUninitialize`.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)