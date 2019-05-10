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
ms.openlocfilehash: fcc2a7322397537c9585d0aaa2674e1d3ab3c656
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460700"
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

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Практическое руководство. Создание ассоциации между классами LINQ to SQL (реляционный конструктор объектов)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)