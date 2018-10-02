---
title: Свойство &lt;имя свойства&gt; невозможно удалить | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22884e69c4802ec0bf699e383f0339d840f515e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559297"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Свойство &lt;имя свойства&gt; не может быть удалена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [свойство &lt;имя свойства&gt; не удается удалить](https://docs.microsoft.com/visualstudio/data-tools/the-property-property-name-cannot-be-deleted).  
  
  
Свойство \<имя свойства > невозможно удалить, так как оно задано как свойство дискриминатора для наследования между \<имя класса > и \<имя класса >  
  
 Выбранное свойство имеет значение **Свойство дискриминатора** для наследования между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в конфигурации наследования между классами данных.  
  
 Задайте **Свойство дискриминатора** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  В реляционном конструкторе объектов выберите линию наследования, которая соединяет классы данных, указанные в сообщении об ошибке.  
  
2.  Задайте **дискриминатора** свойство другое свойство.  
  
3.  Попытайтесь снова удалить свойство.  
  
## <a name="see-also"></a>См. также  
 [Практическое: Настройка наследования с помощью реляционного конструктора объектов](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Наследование классов данных (реляционный конструктор объектов)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Пошаговое руководство. Создание классов LINQ to SQL с использованием наследования с одной таблицей (реляционный конструктор объектов)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)

