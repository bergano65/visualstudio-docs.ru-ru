---
title: Упрощение выражения LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251361"
---
# <a name="simplify-linq-expression"></a>Упрощение выражения LINQ

Область применения этого рефакторинга:

- C#

**Что?** Экземпляры выполнения рефакторинга `SomeEnumerableType.Where(<LambdaExpression>).Single()` в `SomeEnumerable.Single(<LambdaExpression>)` для `Enumerable.Single()`, а также следующие методы Enumerable: `SingleOrDefault()`, `Last()`, `LastOrDefault()`, `Any()`, `Count()`, `First()` и `FirstOrDefault()`.

**Когда?**  Все экземпляры, в которых метод вызывает `Single()`, `SingleOrDefault()` и т. д., не имеют аргументов, и перед ними указывается выражение `Where()`. Входные данные для выражения `Where()` не могут быть построены в виде дерева выражения.

**Зачем?** Удаление ненужного вызова Enumerable для метода `.Where()` повышает производительность и удобочитаемость.

## <a name="how-to"></a>Практическое руководство

1. Поместите курсор в экземпляр `SomeEnumerableType.Where(<LambdaExpression>).Single()` в Visual Studio.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Упростить выражение LINQ**

   ![Преобразование typeof в nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
