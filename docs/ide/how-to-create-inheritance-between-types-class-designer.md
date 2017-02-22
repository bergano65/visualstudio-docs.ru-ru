---
title: "How to: Create Inheritance Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritanceline"
helpviewer_keywords: 
  - "inheritance, relationship defining"
  - "relationships, defining inheritance"
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
caps.handback.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create Inheritance Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Чтобы создать отношение наследования между двумя типами на диаграмме классов, используя Конструктор классов, соедините базовый тип с производными типами.  Отношение наследования может существовать между двумя классами, между классом и интерфейсом или между двумя интерфейсами.  
  
### Создание наследования между типами  
  
1.  В Обозревателе решений выберите проект и откройте файл схемы классов \(CD\-файл\).  
  
     Если диаграмма классов не существует, создайте ее.  См. раздел [How to: Add Class Diagrams to Projects \(Class Designer\)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  На **Панели инструментов** в разделе **Конструктор классов** щелкните элемент **Наследование**.  
  
3.  На диаграмме классов нарисуйте линию наследования между нужными типами, начав с:  
  
    -   производного класса, связав его с базовым классом;  
  
    -   класса реализации, связав его с реализованным интерфейсом;  
  
    -   расширяемого интерфейса, связав его с расширенным интерфейсом.  
  
4.  Если производный тип основан на универсальном типе, можно щелкнуть линию наследования.  В окне **Свойства** задайте свойство **Аргументы типа** в соответствии с типом, который необходим для универсального типа.  
  
    > [!NOTE]
    >  Если родительский абстрактный класс содержит хотя бы один абстрактный член, то все абстрактные члены реализуются как неабстрактные наследующие классы.  См. раздел [Implementing Abstract Base Classes](../ide/refactoring-classes-and-types-class-designer.md#ImplementingAbstractBaseClasses).  
    >   
    >  Хотя вы можете визуализировать существующие универсальные типы, создавать новые универсальные типы нельзя.  Вы также не можете изменить параметры существующих универсальных типов.  
  
## См. также  
 [Наследование](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [How to: View Inheritance Between Types \(Class Designer\)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Visual C\+\+ Classes in Class Designer](../ide/visual-cpp-classes-in-class-designer.md)