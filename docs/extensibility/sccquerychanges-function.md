---
title: "Функция SccQueryChanges | Microsoft Docs"
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
  - "SccQueryChanges"
helpviewer_keywords: 
  - "Функция SccQueryChanges"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccQueryChanges
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция Перечисляет заданный список файлов, предоставляя сведения об изменениях имя для каждого файла через функцию обратного вызова.  
  
## Синтаксис  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### Параметры  
 pContext  
 \[in\] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 \[in\] Число файлов в `lpFileNames` массива.  
  
 lpFileNames  
 \[in\] Массив имен файлов, о котором требуется получить сведения.  
  
 pfnCallback  
 \[in\] Функция обратного вызова для каждого имени файла в списке \(см. [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Подробные сведения\).  
  
 pvCallerData  
 \[in\] Значение, которое будет передано не изменяется, чтобы функция обратного вызова.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Процесс запроса успешно завершена.|  
|SCC\_E\_PROJNOTOPEN|Проект не был открыт в системе управления версиями.|  
|SCC\_E\_ACCESSFAILURE|Произошла ошибка при доступе к системе управления версиями, вероятно, из\-за проблемы с сетью или конфликтов.|  
|SCC\_E\_NONSPECIFICERROR|Произошла неизвестная или общие ошибка.|  
  
## Заметки  
 Запрашиваемый изменяются в пространство имен: в частности, переименование, добавление и удаление файла.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Коды ошибок](../extensibility/error-codes.md)