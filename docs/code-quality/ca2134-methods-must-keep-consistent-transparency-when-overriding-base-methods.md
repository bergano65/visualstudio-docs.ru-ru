---
title: CA2134. Методы должны сохранять одинаковую прозрачность при переопределении базовых методов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31fc319e5edff3e7ea8ddece393ed2ef523e1e84
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912092"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134. Методы должны сохранять одинаковую прозрачность при переопределении базовых методов

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило срабатывает, когда метод, помеченный атрибутом <xref:System.Security.SecurityCriticalAttribute> переопределяет прозрачный метод или метод, помеченные с <xref:System.Security.SecuritySafeCriticalAttribute>. Это правило также применяется, когда прозрачный метод или метод, помеченные с <xref:System.Security.SecuritySafeCriticalAttribute> переопределяет метод, отмеченный атрибутом <xref:System.Security.SecurityCriticalAttribute>.

 Это правило применяется при переопределении виртуального метода или реализации интерфейса.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает при попытках изменить уровень доступности метода вверх по цепочке наследования. Например если виртуальный метод в базовом классе является прозрачным или надежным с точки зрения, затем производного класса необходимо переопределить его с прозрачный или безопасный метод. И наоборот Если виртуальный метод является критически важным для безопасности, производный класс должен переопределять его с к критическому методу безопасности. То же правило применяется для реализации методов интерфейса.

 Правила прозрачности применяются в том случае, когда код JIT-компиляцию, а не во время выполнения, поэтому расчет прозрачности не поддерживает динамическую информацию о типе. Таким образом результат расчета прозрачности должен иметь возможность определить исключительно из статических типов, JIT-компиляции, независимо от динамического типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените прозрачность метода, который переопределяет виртуальный метод или путем реализации интерфейса в соответствии с прозрачностью виртуального метода или метода интерфейса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать предупреждения из этого правила. Нарушение этого правила приведет к в среде выполнения, <xref:System.TypeLoadException> для сборок, которые используют прозрачность уровня 2.

## <a name="examples"></a>Примеры

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>См. также
 [Прозрачный с точки зрения безопасности код, уровень 2](/dotnet/framework/misc/security-transparent-code-level-2)