---
title: "Перечислитель код состояния файла | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "именованные константы, перечислитель SccStatus"
  - "Источник подключаемые модули управления, перечисление состояния файла"
  - "Перечислитель SccStatus"
  - "Перечислитель код состояния файла"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Перечислитель код состояния файла
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`SccStatus` Перечислитель содержит именованные константы, определяющие состояние файла в системе управления версиями. Это перечисление используется с [SccQueryInfo](../extensibility/sccqueryinfo-function.md) и `POPLISTFUNC` функции обратного вызова \(в разделе [POPLISTFUNC](../extensibility/poplistfunc.md) Подробные сведения\).  
  
## Синтаксис  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## Участники  
 SCC\_STATUS\_INVALID  
 Не удалось получить состояние; не следует полагаться на него.  
  
 SCC\_STATUS\_NOTCONTROLLED  
 Файл не существует в системе управления версиями.  
  
 SCC\_STATUS\_CONTROLLED  
 Файл находится в системе управления версиями.  
  
 SCC\_STATUS\_CHECKEDOUT  
 Извлечен текущим пользователем, на локальном диске.  
  
 SCC\_STATUS\_OUTOTHER  
 Файл извлечен другим пользователем.  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 Файл извлечен монопольном режиме.  
  
 SCC\_STATUS\_OUTMULTIPLE  
 Файл извлечен более чем одним пользователем.  
  
 SCC\_STATUS\_OUTOFDATE  
 Файл не является последней.  
  
 SCC\_STATUS\_DELETED  
 Файл был удален из проекта.  
  
 SCC\_STATUS\_LOCKED  
 Файл заблокирован; Дополнительные версии не допускается.  
  
 SCC\_STATUS\_MERGED  
 Файл слияния, но еще не фиксированной и проверен.  
  
 SCC\_STATUS\_SHARED  
 Файл является общим для нескольких проектов.  
  
 SCC\_STATUS\_PINNED  
 Файл будет доступно для явного версии.  
  
 SCC\_STATUS\_MODIFIED  
 Файл был изменен или разделить или нарушении.  
  
 SCC\_STATUS\_OUTBYUSER  
 Файл извлечен текущим пользователем.  
  
 SCC\_STATUS\_NOMERGE  
 Файл не может быть объединена с и не требуется сохранять перед GET.  
  
 SCC\_STATUS\_RESERVED\_1  
 Зарезервировано для внутреннего использования.  
  
 SCC\_STATUS\_RESERVED\_2  
 Зарезервировано для внутреннего использования.  
  
## См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)