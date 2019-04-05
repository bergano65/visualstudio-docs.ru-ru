---
title: Свойство &lt;имя свойства&gt; невозможно удалить | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9d3533f2eb6cfb5bc2e3a68370f48daa4acfc1e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978522"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Свойство &lt;имя свойства&gt; не может быть удалена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Свойство \<имя свойства > невозможно удалить, так как оно задано как свойство дискриминатора для наследования между \<имя класса > и \<имя класса >  
  
 Выбранное свойство назначено в качестве **свойства дискриминатора** для наследования между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в конфигурации наследования между классами данных.  
  
 Установите в качестве **свойства дискриминатора** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  В реляционном конструкторе объектов выберите линию наследования, которая соединяет классы данных, указанные в сообщении об ошибке.  
  
2.  Задайте в качестве свойства **дискриминатора** другое свойство.  
  
3.  Попытайтесь снова удалить свойство.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Настройка наследования с помощью реляционного конструктора объектов](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Наследование классов данных (реляционный конструктор объектов)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Пошаговое руководство: Создание Классов LINQ to SQL с помощью однотабличного наследования (реляционный конструктор объектов)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
