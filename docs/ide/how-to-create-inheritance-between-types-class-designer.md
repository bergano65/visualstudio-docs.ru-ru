---
title: "Практическое руководство. Создание наследования между типами (конструктор классов) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: bd4969c26d1cc0043945189bd4da3acbf5792107
ms.contentlocale: ru-ru
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Практическое руководство. Создание наследования между типами (конструктор классов)
Чтобы создать отношение наследования между двумя типами на диаграмме классов, используя Конструктор классов, соедините базовый тип с производными типами. Отношение наследования может существовать между двумя классами, между классом и интерфейсом или между двумя интерфейсами.  
  
### <a name="to-create-an-inheritance-between-types"></a>Создание наследования между типами  
  
1.  В Обозревателе решений выберите проект и откройте файл схемы классов (CD-файл).  
  
     Если диаграмма классов не существует, создайте ее. См. раздел [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  На **панели инструментов** в разделе **Конструктор классов** щелкните элемент **Наследование**.  
  
3.  На диаграмме классов нарисуйте линию наследования между нужными типами, начав с:  
  
    -   производного класса, связав его с базовым классом;  
  
    -   класса реализации, связав его с реализованным интерфейсом;  
  
    -   расширяемого интерфейса, связав его с расширенным интерфейсом.  
  
4.  Если производный тип основан на универсальном типе, можно щелкнуть линию наследования. В окне **Свойства** задайте свойство **Аргументы типа** в соответствии с типом, который необходим для универсального типа.  
  
    > [!NOTE]
    >  Если родительский абстрактный класс содержит хотя бы один абстрактный член, то все абстрактные члены реализуются как неабстрактные наследующие классы.  
    >   
    >  Хотя вы можете визуализировать существующие универсальные типы, создавать новые универсальные типы нельзя. Вы также не можете изменить параметры существующих универсальных типов.  
  
## <a name="see-also"></a>См. также  
 [Наследование](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Практическое руководство. Просмотр отношения наследования между типами (конструктор классов)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Классы Visual C++ в конструкторе классов](../ide/visual-cpp-classes-in-class-designer.md)
