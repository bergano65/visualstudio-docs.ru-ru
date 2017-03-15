---
title: "Метод NotifyDebuggerOfWaitCompletion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Метод NotifyDebuggerOfWaitCompletion, класс задачи [обработчиков отладки платформы .NET Framework]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод NotifyDebuggerOfWaitCompletion
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Заполнитель метод используется в качестве цели точки останова в отладчике. Этот метод не должен быть встроенными или оптимизированного.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
## Синтаксис  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## Заметки  
 Этот метод следует вызывать все операции соединения с задачей, при их отладчик уведомлений бита.  
  
## Требования  
  
## См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)