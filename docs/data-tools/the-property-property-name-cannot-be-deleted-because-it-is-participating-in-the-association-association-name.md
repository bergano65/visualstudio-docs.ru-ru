---
title: Не удается удалить свойство, так как оно участвует в ассоциации
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ed6b14f64d16d1f18d4b358761169c3d424cee8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174066"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Свойство &lt;имя свойства&gt; невозможно удалить, так как оно участвует в ассоциации &lt;имя ассоциации&gt;

Выбранное свойство имеет значение **свойство ассоциации** для ассоциации между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в ассоциации между классами данных.

Задайте **свойство ассоциации** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Выберите линию ассоциацию, на **реляционный конструктор объектов** , соединяет классы данных, указанные в сообщении об ошибке.

2. Дважды щелкните строку, чтобы открыть **Редактор ассоциаций** диалоговое окно.

3. Удалите свойство из **свойства ассоциации**.

4. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)