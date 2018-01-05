---
title: "CA1009: Правильно объявите обработчики событий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8e72f10ef44c784af98628f4b0c1ed3b72814977
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: правильно объявите обработчики событий
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Делегат, обрабатывающий событие открытый или защищенный не имеет правильной сигнатуры, типа возвращаемого значения или имена параметров.  
  
## <a name="rule-description"></a>Описание правила  
 Методы обработчиков событий принимают два параметра. Первый — типа <xref:System.Object?displayProperty=fullName> и называется «sender». Это объект, вызвавший событие. Второй параметр имеет тип <xref:System.EventArgs?displayProperty=fullName> и называется «e». Это данные, связанные с событием. Например если событие вызывается каждый раз, когда файл открывается, данные события обычно содержит имя файла.  
  
 Методы обработки событий не должны возвращать значение. В языке программирования C# оно обозначается типом возвращаемого `void`. Обработчик событий может вызывать несколько методов в нескольких объектах. Если будет разрешено методы возвращают значение, может произойти несколько значений для каждого события и бы быть доступны только значение последней вызываемый метод.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, исправьте подпись, тип возвращаемого значения или имена параметров делегата. Дополнительные сведения см. следующий пример.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано делегат, который подходит для обработки событий. Методы, которые могут быть вызваны, этот обработчик событий соответствует подписи, которая указана в руководствах по разработке. `AlarmEventHandler`является именем типа делегата. `AlarmEventArgs`является производным от базового класса для данных события <xref:System.EventArgs>, и содержит предупреждения данные события.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2109: проверьте видимые обработчики событий](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Обработка и вызов событий](/dotnet/standard/events/index)  