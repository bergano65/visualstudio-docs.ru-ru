---
title: предупреждения удобства обслуживания
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 340d57df4223cab134ef5cf46180dd1a8c552c08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887154"
---
# <a name="maintainability-warnings"></a>предупреждения удобства обслуживания

Предупреждения удобства обслуживания поддерживает сопровождение библиотек и приложений.

## <a name="in-this-section"></a>В этом разделе

| Правило | Описание |
|-----------|-----------------------------------|
| [CA1500: имена переменных не должны совпадать с именами полей](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Метод экземпляра объявляет параметр или локальную переменную, имя которого совпадает с именем поля экземпляра объявляющего типа, что приводит к ошибкам. |
| [CA1501: избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md) | Тип расположен глубже четырех уровней в иерархии наследования. Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать. |
| [CA1502: избегайте чрезмерной сложности](../code-quality/ca1502-avoid-excessive-complexity.md) | Это правило измеряет число линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей. |
| [CA1504: проверьте имена полей, которые могут ввести в заблуждение](../code-quality/ca1504-review-misleading-field-names.md) | Имя поля экземпляра начинается с «s_» или имя статического (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) поля начинается с «m_». |
| [CA1505: избегайте кода, неудобного для поддержки](../code-quality/ca1505-avoid-unmaintainable-code.md) | Тип или метод имеет низкий индекс обслуживаемости. Низкий индекс удобства поддержки означает, что тип или метод, вероятно, трудно поддерживать, поэтому их следует переработать. |
| [CA1506: избегайте чрезмерного соединения классов](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе. |

## <a name="see-also"></a>См. также

- [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)