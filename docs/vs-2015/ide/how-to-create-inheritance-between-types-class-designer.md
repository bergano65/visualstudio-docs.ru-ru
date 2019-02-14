---
title: Как выполнить Создание наследования между типами (конструктор классов) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1c5b5d75dedf45988291459ed55b31bf80fc583
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760242"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Практическое руководство. Создание наследования между типами (конструктор классов) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также раздел  
 [Наследование](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)   
 [Основы наследования](http://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)   
 [Практическое руководство. Просмотр отношения наследования между типами (конструктор классов)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Классы Visual C++ в конструкторе классов](../ide/visual-cpp-classes-in-class-designer.md)
