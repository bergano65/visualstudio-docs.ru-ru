---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Конструктор классов позволяет реализовать интерфейс на схеме классов путем подключения интерфейса к классу, который предоставляет код для методов интерфейса.  Конструктор классов создает реализацию интерфейса и отображает отношение между интерфейсом и классом как отношение наследования.  Чтобы реализовать интерфейс, необходимо нарисовать линию наследования между интерфейсом и классом или перетащить интерфейс из окна классов.  
  
> [!TIP]
>  Интерфейсы создаются точно так же, как и другие типы.  Если интерфейс существует, но не отображается на схеме классов, то сначала необходимо отобразить его.  Дополнительные сведения см. в разделах [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md) и [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md).  
  
### Реализация интерфейса с помощью линии наследования  
  
1.  На схеме классов отобразите интерфейс и класс, который будет реализовать интерфейс.  
  
2.  Нарисуйте линию наследования от класса к интерфейсу.  
  
     К классу будет прикреплена метка с именем интерфейса, идентифицирующим отношение наследования.  Visual Studio создает заглушки для всех членов интерфейса.  
  
 Дополнительные сведения см. в разделе [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### Реализация интерфейса из "Окна классов"  
  
1.  На схеме классов отобразите класс, который будет реализовать интерфейс.  
  
2.  Откройте "Окно классов" и перейдите к интерфейсу.  
  
    > [!TIP]
    >  Если "Окно классов" не открыто, откройте его из меню **Вид**.  Дополнительные сведения об "Окне классов" см. в разделе [Viewing Classes and Their Members](http://msdn.microsoft.com/ru-ru/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Перетащите узел интерфейса к фигуре класса на схеме.  
  
     К классу будет прикреплена метка с именем интерфейса, идентифицирующим отношение наследования.  Visual Studio создает заглушки для всех членов интерфейса. На данном этапе интерфейс реализован.  
  
## См. также  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)