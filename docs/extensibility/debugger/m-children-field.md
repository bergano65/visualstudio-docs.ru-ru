---
title: "m_children поля | Microsoft Docs"
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
  - "поле m_children ContingentProperties класса [обработчиков отладки платформы .NET Framework]"
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# m_children поля
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Список дочерних задач, которые зарегистрированы с помощью этой задачи.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## Заметки  
 Пока выполняется задача, поток, который выполняет задачу следует доступ к этому массиву.  
  
 Если задача завершена, другие потоки могут обращаться к этому полю, пока они не все, добавить в него и что\-либо удалить из него.  
  
## См. также  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)