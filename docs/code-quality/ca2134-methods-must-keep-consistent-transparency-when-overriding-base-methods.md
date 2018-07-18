---
title: 'CA2134: методы должны сохранять согласованную прозрачность при переопределении базовых методов'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c02ce23c341df377bc16b56cdd85769acf5582c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917750"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: методы должны сохранять согласованную прозрачность при переопределении базовых методов
|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило срабатывает, если метод, помеченный атрибутом <xref:System.Security.SecurityCriticalAttribute> переопределяет метод, который является прозрачным или помечены <xref:System.Security.SecuritySafeCriticalAttribute>. Это правило также применяется, когда метод, который является прозрачным или помечены <xref:System.Security.SecuritySafeCriticalAttribute> переопределяет метод, который отмечен атрибутом <xref:System.Security.SecurityCriticalAttribute>.

 Это правило применяется при переопределении виртуального метода или реализации интерфейса.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает при попытках изменить уровень доступности метода вверх по цепочке наследования. Например, если виртуальный метод в базовом классе является прозрачным или критическим, затем производный класс должен переопределять его с прозрачный или безопасный метод. И наоборот Если виртуальный метод является критически важным для безопасности, производный класс должен переопределять его с критический метод безопасности. Это же правило применяется для реализации методов интерфейса.

 Правила прозрачности применяются, когда код JIT-компиляцию, а не во время выполнения, поэтому расчет прозрачности не поддерживает динамические сведения о типе. Таким образом результат вычисления прозрачности необходимо определить исключительно из статических типов, JIT-компиляции, независимо от динамического типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, измените прозрачность метода, который переопределяет виртуальный метод или реализации интерфейса в соответствии с прозрачностью виртуального метода или метода интерфейса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать предупреждения из этого правила. Нарушение этого правила приведет к среде выполнения <xref:System.TypeLoadException> для сборок, использующих прозрачность уровня 2.

## <a name="examples"></a>Примеры

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>См. также
 [Прозрачный с точки зрения безопасности код, уровень 2](/dotnet/framework/misc/security-transparent-code-level-2)