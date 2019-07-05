---
title: предупреждения удобства обслуживания
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752a637ef01c33aa4e93083e9578d01f00977960
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976156"
---
# <a name="maintainability-warnings"></a>Предупреждения, связанные с удобством обслуживания

Предупреждения удобства обслуживания поддерживает сопровождение библиотек и приложений.

## <a name="in-this-section"></a>Содержание раздела

| Правило | Описание |
|-----------|-----------------------------------|
| [CA1500: Имена переменных не должны совпадать с именами полей](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Метод экземпляра объявляет параметр или локальную переменную, имя которого совпадает с именем поля экземпляра объявляющего типа, что приводит к ошибкам. |
| [CA1501: Избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md) | Тип расположен глубже четырех уровней в иерархии наследования. Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать. |
| [CA1502: Избегайте чрезмерной сложности](../code-quality/ca1502-avoid-excessive-complexity.md) | Это правило измеряет число линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей. |
| [CA1504: Проверьте имена полей, вводит в заблуждение](../code-quality/ca1504-review-misleading-field-names.md) | Имя поля экземпляра начинается с «s_» или имя статического (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) поля начинается с «m_». |
| [CA1505: Избегайте кода, неудобного для поддержки](../code-quality/ca1505-avoid-unmaintainable-code.md) | Тип или метод имеет низкий индекс обслуживаемости. Низкий индекс удобства поддержки означает, что тип или метод, вероятно, трудно поддерживать, поэтому их следует переработать. |
| [CA1506: Избегайте чрезмерного соединения классов](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе. |
| [CA1507: Используйте nameof вместо строки](../code-quality/ca1507.md) | Строковый литерал используется в качестве аргумента где `nameof` выражение может быть использовано. |

## <a name="see-also"></a>См. также

- [Меру сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md)