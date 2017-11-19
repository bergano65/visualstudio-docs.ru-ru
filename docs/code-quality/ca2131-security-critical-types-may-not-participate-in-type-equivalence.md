---
title: "CA2131: Типы критической безопасности могут не участвовать в эквивалентности типов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 90789a7a632084d157f94f72deb1c06370223056
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: типы критической безопасности могут не участвовать в эквивалентности типа
|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип участвует в эквивалентности типов и либо сам тип или член или поле типа помечается <xref:System.Security.SecurityCriticalAttribute> атрибута.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило применяется ко всем критическим типам или к типам, содержащим критические методы или поля, участвующие в эквивалентности типов. Когда среда CLR обнаруживает такой тип, она не загружает его с <xref:System.TypeLoadException> во время выполнения. Обычно это правило срабатывает, только если пользователи реализуют эквивалентность типов вручную вместо того, чтобы позволить tlbimp и компиляторам обработать эквивалентность типов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите атрибут SecurityCritical.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующих примерах демонстрируется интерфейс, метод и поле, вызывающие срабатывание этого правила.  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Прозрачный с точки зрения безопасности код, уровень 2](http://msdn.microsoft.com/Library/4d05610a-0da6-4f08-acea-d54c9d6143c0)