---
title: "CA2241: Предоставьте правильные аргументы методам форматирования | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 20952c22f7449e7e19880f6f89f87d5d34bf8ee9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: предоставьте правильные аргументы методам форматирования
|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 `format` Строковый аргумент, переданного методу, таких как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, или <xref:System.String.Format%2A?displayProperty=fullName> не содержит элемент форматирования, соответствующий каждому аргументу объекта, или наоборот.  
  
## <a name="rule-description"></a>Описание правила  
 Аргументы для методов, таких как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, и <xref:System.String.Format%2A> представляют собой строку форматирования, следуют несколько <xref:System.Object?displayProperty=fullName> экземпляров. Строка формата состоит из текста и внедренного форматирование элементов в формате {индекса [, выравнивание] [: formatString]}. 'index' — это отсчитываемое от нуля целое число, которое указывает форматируемый объект. Если объект не имеет соответствующий индекс в строке формата, объект учитывается. Если объект, указанный свойством «index» не существует, <xref:System.FormatException?displayProperty=fullName> во время выполнения возникает исключение.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, предоставляет элемента формата для каждого аргумента объекта и аргумент объекта для каждого элемента форматирования.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано два нарушения данного правила.  
  
 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]