---
title: Свойство не может быть удалено, так как оно участвует в ассоциации
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e1890535fb008c8e8be6ee9dea0eda3ab3844da6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648148"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Нельзя удалить свойство &lt;имя свойства&gt;, поскольку оно участвует в ассоциации &lt;имя ассоциации&gt;

Выбранное свойство имеет значение **Свойство ассоциации** для ассоциации между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в ассоциации между классами данных.

Установите **Свойство ассоциации** на другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. В **реляционном конструкторе объектов** выберите линию связи, которая соединяет классы данных, указанные в сообщении об ошибке.

2. Дважды щелкните по линии связи, чтобы открыть диалоговое окно **Редактор ассоциаций**.

3. Удалите свойство из **Свойств ассоциации**.

4. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)