---
title: 'CA1903: использовать API-интерфейс только из целевой исполняющей среды'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4f49c8a4da3ad746e5221bb689285c89d48e6e1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: использовать API-интерфейс только из целевой исполняющей среды
|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Категория|Microsoft.Portability|
|Критическое изменение|Критическое — цифровой подписи, доступного для элемента или типа.<br /><br /> Не критическое — при возникновении в теле метода.|

## <a name="cause"></a>Причина
 Член или тип использует член или тип, который появился в пакете обновления, не включенном в целевую среду проекта.

## <a name="rule-description"></a>Описание правила
 Новые элементы и типы были включены в .NET Framework 2.0 с пакетом обновления 1 и 2, .NET Framework 3.0 с пакетом обновления 1 и 2 и платформа .NET Framework 3.5 с пакетом обновления 1. Проекты, предназначенные для основных версий платформы .NET Framework, могут непреднамеренно иметь зависимости от этих новых API. Чтобы предотвратить эту зависимость, это правило срабатывает при обнаружении новых членов и типов, которые не были включены по умолчанию с целевой платформы проекта.

 **Требуемая версия .NET Framework и зависимости пакетов службы**

|||
|-|-|
|Целевая платформа|Возникает при обнаружении членов, появившиеся в|
|.NET Framework 2.0|.NET framework 2.0 SP1, .NET Framework 2.0 с пакетом обновления 2|
|.NET Framework 3.0|.NET framework 2.0 SP1, SP2 .NET Framework 2.0, .NET Framework 3.0 с пакетом обновления 1, .NET Framework 3.0 с пакетом обновления 2|
|.NET Framework 3,5|.NET Framework 3.5 SP1|
|.NET Framework 4|Н/Д|

 Для изменения целевой платформы проекта. в разделе [предназначенных для версии .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы удалить зависимость от пакета обновления, удалите все случаи использования нового члена или типа. Если зависимость добавлена специально отключить предупреждение, или отключить это правило.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если это не было намеренным зависимость от указанного пакета обновления. В этом случае приложение может не работать в системах, не установлен пакет обновления. Отключить предупреждение, или отключить это правило, если бы это был умышленно зависимостей.

## <a name="example"></a>Пример
 В следующем примере класс, который использует тип DateTimeOffset, доступен только в .NET 2.0 с пакетом обновления 1. В этом примере требуется, что .NET Framework 2.0 был выбран в раскрывающемся списке требуемой версии .NET Framework в свойствах проекта.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Пример
 В следующем примере устраняется нарушение, описанное выше, заменив случаи использования типа DateTimeOffset с типом DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>См. также
 [Предупреждения переносимости](../code-quality/portability-warnings.md) [предназначенных для конкретной версии .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)