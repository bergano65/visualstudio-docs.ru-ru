---
title: "Функция SccWillCreateSccFile | Microsoft Docs"
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
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "Функция SccWillCreateSccFile"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccWillCreateSccFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция определяет, поддерживает ли подключаемый модуль системы управления версиями, создание MSSCCPRJ. Файл SCC для каждого заданного файла.  
  
## Синтаксис  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### Параметры  
 pContext  
 \[in\] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 \[in\] Количество имен файлов, включенных в `lpFileNames` массива, а также длину `pbSccFiles` массива.  
  
 lpFileNames  
 \[in\] Массив имен полным путем к файлу для проверки \(массива должен быть выделен вызывающим объектом\).  
  
 pbSccFiles  
 \[in, out\] Массив, в котором сохраняются результаты.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Выполнено.|  
|SCC\_E\_INVALIDFILEPATH|Один из путей в массиве является недопустимым.|  
|SCC\_E\_NONSPECIFICERROR|Неспецифическая ошибка.|  
  
## Заметки  
 Эта функция вызывается со списком файлов для определения, если подключаемый модуль системы управления версиями обеспечивает поддержку в MSSCCPRJ. Файл SCC для каждого заданного файлов \(Подробнее о MSSCCPRJ. Файл SCC см. [MSSCCPRJ. Файл SCC](../extensibility/mssccprj-scc-file.md)\). Подключаемые модули управления версиями можно объявить, имеют ли они возможность создания MSSCCPRJ. Файлы SCC, объявив `SCC_CAP_SCCFILE` во время инициализации. Подключаемый модуль возвращает `TRUE` или `FALSE` каждого файла в `pbSccFiles` массива, указывающая, что файлы данного MSSCCPRJ. Поддержка SCC. Если подключаемый модуль возвращает успех код из функции, учитываются значения из возвращаемого массива. В случае сбоя массив учитывается.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ. Файл SCC](../extensibility/mssccprj-scc-file.md)