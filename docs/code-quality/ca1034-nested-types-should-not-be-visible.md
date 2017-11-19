---
title: "CA1034: Вложенные типы не должны быть видимыми | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb549e50f33ac172f1eaa0e2a4489cd1900d0542
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: вложенные типы не должны быть видимыми
|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Видимый извне тип содержит объявление видимого типа. Вложенных перечислений и защищенные типы будут исключены из этого правила.  
  
## <a name="rule-description"></a>Описание правила  
 Вложенный тип — это тип, объявленный внутри области другого типа. Вложенные типы полезны для инкапсуляции закрытых сведений о реализациях содержащего типа. В силу этого вложенные типы не должны быть видимыми для внешнего кода.  
  
 Не используйте вложенные типы, видимые извне для логической группировки или во избежание конфликтов имен. Вместо этого используйте пространства имен.  
  
 Вложенные типы включают понятие доступности членов некоторые программисты не всегда очевидно.  
  
 Защищенные типы можно использовать в подклассах, а вложенные типы в сценариях расширенной настройки.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Если вложенный тип, видимый извне не требуется, измените доступность типов. В противном случае удалите вложенный тип из своего родителя. Если целью вложения является категоризация вложенных типов, необходимо используйте пространство имен для создания иерархии.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]