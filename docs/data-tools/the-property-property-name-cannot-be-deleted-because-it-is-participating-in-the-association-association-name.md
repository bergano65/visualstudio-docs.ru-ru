---
title: Не удается удалить свойство, так как оно участвует в ассоциации
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9e65049ae881ff11cd647fe09df3a6919dd8818c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Свойство &lt;имя свойства&gt; невозможно удалить, так как оно участвует в ассоциации &lt;имя связи&gt;

Выбранное свойство имеет значение **свойство ассоциации** для ассоциации между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в ассоциации между классами данных.

Задать **свойство ассоциации** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. В реляционном конструкторе объектов выберите линию ассоциацию, которая соединяет классы данных, указанные в сообщении об ошибке.

2. Дважды щелкните строку, чтобы открыть **Редактор ассоциаций** диалоговое окно.

3. Удалите свойство из **свойства ассоциации**.

4. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)