---
title: "обращение поля | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "поле обращение, класс задачи [обработчиков отладки платформы .NET Framework]"
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# обращение поля
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Делегат, который представляет код, выполняемый в <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.field assembly object m_action  
```  
  
## Заметки  
 Это `action` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструктора.  
  
## См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)