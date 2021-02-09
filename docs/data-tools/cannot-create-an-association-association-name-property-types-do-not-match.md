---
title: Типы свойств не совпадают
description: Не удается создать тип ассоциации-свойство не соответствует. Просмотрите сведения об этом сообщении Visual Studio реляционный конструктор объектов (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 0a75d16d79359db7fa2db2e68db23d693d7f2721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859233"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Невозможно создать ассоциацию &lt;имя ассоциации&gt; — типа свойств не совпадают

Не удается создать \<association name> тип ассоциации-свойство не соответствует. Свойства не имеют совпадающих типов: \<property names> .

Ассоциации определяются выбранными **свойствами ассоциации** в диалоговом окне **Редактор ассоциаций**. Свойства на каждой стороне ассоциации должны иметь одинаковый тип данных.

Свойства, перечисленные в сообщении не имеют одинаковых типов данных.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Проверьте сообщение и отметьте свойства, указанные в сообщении.

2. Нажмите кнопку **OK**, чтобы закрыть диалоговое окно.

3. Проверьте **Свойства ассоциации** и выберите свойства с одинаковым типом данных.

4. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Как создать ассоциацию между классами LINQ to SQL (реляционный конструктор R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)