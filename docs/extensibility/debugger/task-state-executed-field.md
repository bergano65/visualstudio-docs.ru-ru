---
title: "Поле TASK_STATE_EXECUTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Поле TASK_STATE_EXECUTED, класс задачи [обработчиков отладки платформы .NET Framework]"
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Поле TASK_STATE_EXECUTED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задача выполняется, но еще не завершилась.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## Заметки  
 Если [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) поле содержит это значение <xref:System.Threading.Tasks.Task.Status%2A> возвращает <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)