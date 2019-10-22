---
title: Не удается создать ассоциацию &lt;association имя &gt;-Property в списке дважды | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e4a1d20b5c341c1643836ae30e5de6243f35454
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662557"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Не удалось создать ассоциацию &lt;имя ассоциации&gt; — одно и то же свойство перечислено дважды
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Не удалось создать ассоциацию \<имя ассоциации>. Одно и то же свойство присутствует в списке несколько раз: \<имя свойства>.

 Ассоциации определяются выбранными **свойствами ассоциации** в диалоговом окне **Редактор ассоциаций**. Свойства могут быть перечислены только один раз для каждого класса в ассоциации.

 Свойство в сообщении появляется более чем один раз в любом родительском или дочернем окне **Свойства ассоциации**.

### <a name="to-resolve-this-condition"></a>Чтобы устранить эту проблему,

- Проверьте сообщение и отметьте свойство, указанное в сообщении.

- Нажмите кнопку **ОК**, чтобы закрыть окно сообщения.

- Проверьте **Свойства ассоциации** и удалите дублированные записи.

- Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также раздел
 [Средства LINQ to SQL в Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186) [Практическое руководство. Создание ассоциации (отношения) между LINQ to SQL классами (реляционный конструктор r)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [Пошаговое руководство. Создание классов LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
