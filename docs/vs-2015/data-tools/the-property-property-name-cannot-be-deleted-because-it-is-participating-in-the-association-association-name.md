---
title: Свойство &lt;имя свойства&gt; невозможно удалить, так как оно участвует в ассоциации &lt;имя ассоциации&gt; | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a3ba746f9e4dcd8da45a002c5c763384558342ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053914"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Нельзя удалить свойство &lt;имя свойства&gt;, поскольку оно участвует в ассоциации &lt;имя ассоциации&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Выбранное свойство имеет значение **Свойство ассоциации** для ассоциации между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в ассоциации между классами данных.  
  
 Установите **Свойство ассоциации** на другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. В реляционном конструкторе объектов выберите линию ассоциацию, которая соединяет классы данных, указанные в сообщении об ошибке.  
  
2. Дважды щелкните по линии связи, чтобы открыть диалоговое окно **Редактор ассоциаций**.  
  
3. Удалите свойство из **Свойств ассоциации**.  
  
4. Попытайтесь снова удалить свойство.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Практическое руководство. Создать ассоциацию (связь) между классами LINQ to SQL (реляционный конструктор объектов)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
