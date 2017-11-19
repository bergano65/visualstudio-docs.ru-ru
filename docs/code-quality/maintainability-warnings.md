---
title: "Предупреждения удобства обслуживания | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 88199541fe5d3c4be3f9f1cff6de308d45d0d85a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="maintainability-warnings"></a>предупреждения удобства обслуживания
Предупреждения удобства обслуживания поддерживает сопровождение библиотек и приложений.  
  
## <a name="in-this-section"></a>Содержание  
  
|Правило|Описание|  
|----------|-----------------|  
|[CA1500: имена переменных не должны совпадать с именами полей](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Метод экземпляра объявляет параметр или локальную переменную, имя которого совпадает с именем поля экземпляра объявляющего типа, который приводит к ошибкам.|  
|[CA1501: избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md)|Тип расположен глубже четырех уровней в иерархии наследования. Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать.|  
|[CA1502: избегайте чрезмерной сложности](../code-quality/ca1502-avoid-excessive-complexity.md)|Это правило измеряет число линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей.|  
|[CA1504: проверьте имена полей, которые могут ввести в заблуждение](../code-quality/ca1504-review-misleading-field-names.md)|Имя поля экземпляра начинается с «s_» или имя статического (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) поля начинается с «m_».|  
|[CA1505: избегайте кода, неудобного для поддержки](../code-quality/ca1505-avoid-unmaintainable-code.md)|Тип или метод имеет низкий индекс обслуживаемости. Низкий индекс удобства поддержки означает, что тип или метод, вероятно, трудно поддерживать, поэтому их следует переработать.|  
|[CA1506: избегайте чрезмерного соединения классов](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.|  
  
## <a name="see-also"></a>См. также  
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)