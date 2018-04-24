---
title: Не удалось создать ассоциацию - свойство перечислено дважды
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2d183241739df858b52700aef9ed8c065db6bd1a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Не удалось создать ассоциацию &lt;имя ассоциации&gt; -свойство перечислено дважды

Не удалось создать ассоциацию \<имя ассоциации >. Же свойство перечислено более одного раза: \<имя свойства >.

Ассоциации определяются выбранными **свойства ассоциации** в **Редактор ассоциаций** диалоговое окно. Свойства могут быть перечислены только один раз для каждого класса в ассоциации.

Свойство в сообщении появляется более одного раза в родительского или дочернего класса **свойства ассоциации**.

## <a name="to-resolve-this-condition"></a>Чтобы устранить эту проблему,

- Проверьте сообщение и отметьте свойство, указанное в сообщении.

- Нажмите кнопку **ОК** , чтобы закрыть окно сообщения.

- Проверить **свойства ассоциации** и удалите дублированные записи.

- Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Как: создать ассоциацию между LINQ to SQL classes (O/R-конструктор)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)