---
title: Свойство &lt;имя свойства&gt; невозможно удалить | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 98b065500c9c881a7190b59c4d70a0433eb8864c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186528"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Свойство &lt;имя свойства&gt; не может быть удалена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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

