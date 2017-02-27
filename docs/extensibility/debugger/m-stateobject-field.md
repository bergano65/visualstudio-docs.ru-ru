---
title: "m_stateObject поля | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "поле m_stateObject, класс задачи [обработчиков отладки платформы .NET Framework]"
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# m_stateObject поля
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Объект, представляющий данные, которые будет использовать действие.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.field assembly object m_stateObject  
```  
  
## Заметки  
 Это `state` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструктора. Это также резервное поле для <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Свойства.  
  
## См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)