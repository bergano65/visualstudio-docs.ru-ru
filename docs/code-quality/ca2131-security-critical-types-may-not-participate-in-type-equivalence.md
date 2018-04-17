---
title: 'CA2131: Типы критической безопасности могут не участвовать в эквивалентности типов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 551c0bd73abb2d42f2673dfcc57153b957bcbcbc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 [Прозрачный с точки зрения безопасности код, уровень 2](/dotnet/framework/misc/security-transparent-code-level-2)