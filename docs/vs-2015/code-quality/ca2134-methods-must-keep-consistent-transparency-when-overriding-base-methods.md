---
title: 'CA2134: методы должны иметь постоянную прозрачность при переопределении базовых методов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe9a84280b0124eed6bb0cfffae9c1ec2942bddf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547723"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134. Методы должны сохранять одинаковую прозрачность при переопределении базовых методов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|месодсмустоверридевисконсистенттранспаренци|
|CheckId|CA2134|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило срабатывает, когда метод, помеченный атрибутом, <xref:System.Security.SecurityCriticalAttribute> переопределяет метод, который является прозрачным или помеченным атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> . Правило также срабатывает, когда метод, прозрачный или помеченный с помощью <xref:System.Security.SecuritySafeCriticalAttribute> переопределения, переопределяет метод, помеченный как <xref:System.Security.SecurityCriticalAttribute> .

 Это правило применяется при переопределении виртуального метода или реализации интерфейса.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает при попытке изменить доступ к безопасности метода, расположенного выше по цепочке наследования. Например, если виртуальный метод в базовом классе является прозрачным или безопасным, то производный класс должен переопределять его с помощью прозрачного или безопасного метода. И наоборот, если виртуальный объект является критически важным для безопасности, производный класс должен переопределять его с помощью метода, критического для безопасности. То же правило применяется для реализации методов интерфейса.

 Правила прозрачности применяются, когда код компилируется JIT-компилятором, а не во время выполнения, чтобы в вычислении прозрачности не было сведений о динамическом типе. Таким образом, результат вычисления прозрачности должен быть способен определяться исключительно из статических типов, JIT-скомпилированных, независимо от динамического типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените прозрачность метода, переопределяющего виртуальный метод, или реализуйте интерфейс, чтобы он соответствовал прозрачности виртуального метода или интерфейса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте вывод предупреждений из этого правила. Нарушение этого правила приведет к тому, что среда выполнения будет <xref:System.TypeLoadException> работать для сборок, использующих прозрачность уровня 2.

## <a name="examples"></a>Примеры

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>См. также:
 [Прозрачный с точки зрения безопасности код, уровень 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
