---
title: Не удалось создать ассоциацию — одно и то же свойство перечислено дважды
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9c198518fca543eb9275afd918a640275f797b19
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952623"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Не удалось создать ассоциацию &lt;имя ассоциации&gt; — одно и то же свойство перечислено дважды

Не удалось создать ассоциацию \<имя ассоциации>. Одно и то же свойство присутствует в списке несколько раз: \<имя свойства>.

Ассоциации определяются выбранными **свойствами ассоциации** в диалоговом окне **Редактор ассоциаций**. Свойства могут быть перечислены только один раз для каждого класса в ассоциации.

Свойство в сообщении появляется более чем один раз в любом родительском или дочернем окне **Свойства ассоциации**.

## <a name="to-resolve-this-condition"></a>Чтобы устранить эту проблему,

- Проверьте сообщение и отметьте свойство, указанное в сообщении.

- Нажмите кнопку **ОК**, чтобы закрыть окно сообщения.

- Проверьте **Свойства ассоциации** и удалите дублированные записи.

- Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Практическое: Создание ассоциации между классами LINQ to SQL (реляционный конструктор объектов)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)