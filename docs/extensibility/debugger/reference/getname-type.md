---
title: "GETNAME_TYPE | Microsoft Docs"
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
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "Перечисление GETNAME_TYPE"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет тип имени файлов для извлечения.  
  
## Синтаксис  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```c#  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## Члены  
 GN\_NAME  
 Указывает понятное имя документа или контекста.  
  
 GN\_FILENAME  
 Указывает полный путь документа или контекста.  
  
 GN\_BASENAME  
 Указывает базовое имя файла вместо полного пути документа или контекста.  
  
 GN\_MONIKERNAME  
 Задает уникальное имя документа или контекста в форму моникера.  
  
 GN\_URL  
 Указывает имя URL\-адрес документа или контекста.  
  
 GN\_TITLE  
 Определяет заголовок документа, если он существует.  
  
 GN\_STARTPAGEURL  
 Получает начальный URL\-адрес страницы для процессов.  
  
## Заметки  
 Эти значения передаются в качестве параметров [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)"  [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)и  [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) методы, чтобы определить, какие имя для возврата.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)