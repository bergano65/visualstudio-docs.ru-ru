---
title: "Функция SccAddFilesFromSCC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "Функция SccAddFilesFromSCC"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Функция SccAddFilesFromSCC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция добавляет список файлов из системы управления версиями в открытый проект.  
  
## Синтаксис  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### Параметры  
 pContext  
 \[in\] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 \[in\] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 lpUser  
 \[in, out\] Имя пользователя \(до SCC\_USER\_SIZE, включая завершающий символ null\).  
  
 lpAuxProjPath  
 \[in, out\] Вспомогательный строку, идентифицирующую проекта \(до `SCC_PRJPATH_`размер, включая завершающий символ null\).  
  
 cFiles  
 \[in\] Число файлов, предоставляемых `lpFilePaths`.  
  
 lpFilePaths  
 \[in, out\] Массив имен файлов для добавления в текущий проект.  
  
 lpDestination  
 \[in\] Путь назначения, в которой находятся файлы должны быть записаны.  
  
 lpComment  
 \[in\] Комментарий, применяемый к каждой добавляемой файлов.  
  
 pbResults  
 \[in, out\] Массив флагов, набор в случае успеха \(от нуля или равен TRUE\) или сбоя \(ноль или FALSE\) для каждого файла \(размер массива должен быть по крайней мере `cFiles` long\).  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_E\_PROJNOTOPEN|Проект не открыт.|  
|SCC\_E\_OPNOTPERFORMED|Соединение не в том же проекте, в соответствии с `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|Пользователь не авторизован для обновления базы данных.|  
|SCC\_E\_NONSPECIFICERROR|Произошла неизвестная ошибка.|  
|SCC\_I\_RELOADFILE|Файл или проект должен быть перезагружен.|  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)