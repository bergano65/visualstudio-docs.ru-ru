---
title: "Класс ContingentProperties - внутренние члены | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Класс ContingentProperties [обработчиков отладки платформы .NET Framework]"
  - "отладчики, класс ContingentProperties [платформа .NET Framework]"
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Класс ContingentProperties - внутренние члены
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Содержит дополнительные свойства для <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Поскольку невозможно получить эти внутренние члены из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## Члены  
  
### Поля  
  
|Имя|Описание|  
|---------|--------------|  
|[m\_children](../../extensibility/debugger/m-children-field.md)|Список дочерних задач, которые зарегистрированы с помощью этой задачи.|  
  
## Заметки  
 Платформа .NET Framework инициализирует поля этого класса, только в том случае, если они требуются.  
  
## См. также  
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)