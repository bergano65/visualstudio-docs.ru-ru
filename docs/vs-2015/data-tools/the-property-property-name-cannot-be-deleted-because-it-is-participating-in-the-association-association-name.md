---
title: Не удается удалить свойство &lt;property Name &gt;, так как оно участвует в ассоциации &lt;association имя &gt; | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 53bf12a84a705ddca0cacffc36028698cb08443a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667274"
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

## <a name="see-also"></a>См. также раздел
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [Практическое руководство. Создание ассоциации (отношения) между LINQ to SQL классами (реляционный конструктор r)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [Пошаговое руководство. Создание классов LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
