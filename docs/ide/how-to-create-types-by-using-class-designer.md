---
title: "How to: Create Types by using Class Designer | Microsoft Docs"
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
  - "VS.Clr.ClrAttributesDialog"
helpviewer_keywords: 
  - "custom attributes, applying"
  - "class diagrams, creating types"
  - "classes [Visual Studio], creating with Class Designer"
  - "Class Designer [Visual Studio], creating classes"
  - "types [Visual Studio], class diagrams"
  - "attributes [Visual Studio], applying custom"
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 41
caps.handback.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create Types by using Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для создания новых типов проектов Visual C\# .NET и Visual Basic .NET используйте диаграмму классов.  Сведения о существующих типах см. в статье [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md).  
  
-   [Создание нового типа](#CreateType)  
  
-   [Применение пользовательского атрибута к типу](#CustAttributeType)  
  
-   [Применение пользовательского атрибута к члену типа](#CustAttributeMember)  
  
##  <a name="CreateType"></a> Создание нового типа  
  
1.  В панели инструментов, в конструкторе классов, перетащите в диаграмму классов один из следующих элементов:  
  
    -   **Класс** или **абстрактный класс**  
  
    -   **Enum**  
  
    -   **Интерфейс**  
  
    -   **Структура** \(VB\) или **Struct** \(C\#\)  
  
    -   **Делегат**  
  
    -   **Модуль** \(только VB\)  
  
2.  Задайте имя типа.  Затем выберите для него уровень доступа.  
  
3.  Выберите файл, в который требуется добавить исходный код для типа:  
  
    -   Чтобы создать новый файл и добавить его в текущий проект, выберите **Создать новый файл** и задайте имя файла.  
  
    -   Чтобы добавить код в существующий файл, выберите **Добавить в существующий файл**.  
  
         Если решение содержит общий проект для нескольких приложений, можно добавить новый тип в диаграмму классов в проекте приложения, но только при условии, что соответствующий файл класса находится в том же проекте приложения или в общем проекте.  
  
4.  Затем добавьте другие элементы для указания типа:  
  
    |||  
    |-|-|  
    |**Для**|**Add**|  
    |Классы, абстрактные классы, структуры или struct|Методы, свойства, поля, события, конструкторы \(метод\), деструкторы \(метод\) и константы, определяющие тип|  
    |перечислениям;|Значения поля, составляющие перечисление|  
    |интерфейсов,|Методы, свойства и события, составляющие интерфейс|  
    |Делегат|Параметры, определяющие делегат|  
    |Module|Методы, свойства, поля, события, конструкторы \(метод\), деструкторы \(метод\) и константы, определяющие модуль|  
  
     См. раздел [Создание членов](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Применение пользовательского атрибута к типу  
  
1.  Щелкните фигуру типа на схеме классов.  
  
2.  В окне "Свойства" рядом со свойством **Пользовательские атрибуты** для типа нажмите кнопку с многоточием \(…\).  
  
3.  Добавьте один или несколько настраиваемых атрибутов, по одному на строку.  Не заключайте их в квадратные скобки.  
  
     По завершении пользовательские атрибуты будут применены к типу.  
  
##  <a name="CustAttributeMember"></a> Применение пользовательского атрибута к члену типа  
  
1.  Щелкните на схеме классов имя члена на его фигуре типа или его строку в окне "Сведения о классе".  
  
2.  В окне "Свойства" перейдите к свойству члена **Пользовательские атрибуты**.  
  
3.  Добавьте один или несколько настраиваемых атрибутов, по одному на строку.  Не заключайте их в квадратные скобки.  
  
     По завершении пользовательские атрибуты будут применены к типу.  
  
## См. также  
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Creating and Configuring Type Members \(Class Designer\)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)