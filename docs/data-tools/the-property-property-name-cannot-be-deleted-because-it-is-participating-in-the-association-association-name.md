---
title: Свойство участвует в ассоциации
description: Свойство не может быть удалено, так как оно участвует в ассоциации. Просмотр сведений об этом реляционный конструктор объектов (реляционном конструкторе) сообщения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 99115a3c04aec71e7d000dfa4e707eacb0e28cf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866402"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Нельзя удалить свойство &lt;имя свойства&gt;, поскольку оно участвует в ассоциации &lt;имя ассоциации&gt;

Выбранное свойство имеет значение **Свойство ассоциации** для ассоциации между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в ассоциации между классами данных.

Установите **Свойство ассоциации** на другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Выберите линию связи в **конструкторе O/R** , соединяющем классы данных, указанные в сообщении об ошибке.

2. Дважды щелкните по линии связи, чтобы открыть диалоговое окно **Редактор ассоциаций**.

3. Удалите свойство из **Свойств ассоциации**.

4. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также раздел

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)