---
title: CA2131. Типы критической безопасности могут не участвовать в эквивалентности типов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6fba07fbfd7f0c36681b7567ad01359df1be88f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700525"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131. Критические для безопасности типы не могут участвовать в эквивалентности типов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип участвует в эквивалентности типов и либо сам тип или член или поле типа помечены с <xref:System.Security.SecurityCriticalAttribute> атрибута.

## <a name="rule-description"></a>Описание правила
 Это правило применяется ко всем критическим типам или к типам, содержащим критические методы или поля, участвующие в эквивалентности типов. Когда среда CLR обнаруживает такой тип, его не удается загрузить его с <xref:System.TypeLoadException> во время выполнения. Обычно это правило срабатывает, только если пользователи реализуют эквивалентность типов вручную вместо того, чтобы позволить tlbimp и компиляторам обработать эквивалентность типов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите атрибут SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующих примерах показано, интерфейс, метод и поле, вызывающее срабатывание этого правила.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>См. также
 [Прозрачный с точки зрения безопасности код, уровень 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
