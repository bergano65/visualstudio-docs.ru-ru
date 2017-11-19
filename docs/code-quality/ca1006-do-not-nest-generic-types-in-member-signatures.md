---
title: "CA1006: Не вкладывайте универсальные типы в сигнатурах членов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2ec28ce2cfe1e8c0de622a0f35d37ddd82e1be7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: не вкладывайте универсальные типы в сигнатуры членов
|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Внешне видимый член имеет цифровую подпись, которая содержит аргумент вложенного типа.  
  
## <a name="rule-description"></a>Описание правила  
 Аргумент вложенного типа также является аргументом универсального типа. Чтобы вызвать член, сигнатура которого содержит аргумент вложенного типа, пользователь должен создать экземпляр одного универсального типа и передать этот тип конструктору второго универсального типа. Это приводит к усложнению процедуры и синтаксиса, чего следует избегать.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените структуру удалить аргумент вложенного типа.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Использование универсальных типов в синтаксисе, который легко понять и использовать, сокращает время, необходимое для обучения и ускоряет адаптацию новых библиотек.  
  
## <a name="example"></a>Пример  
 В следующем примере метод, который нарушает правила и синтаксис, необходимый для вызова этого метода.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)