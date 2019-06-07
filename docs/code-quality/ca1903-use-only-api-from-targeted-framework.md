---
title: CA1903. Используйте API только из целевой рабочей среды
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e57607cdfa8790c9b9fd4e692956f7bb823981a
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744860"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903. Используйте API только из целевой рабочей среды

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Категория|Microsoft.Portability|
|Критическое изменение|Критическое — цифровой подписи видимого члена или типа.<br /><br /> Не критическое — при возникновении в теле метода.|

## <a name="cause"></a>Причина
 Член или тип использует член или тип, который появился в пакете обновления, не был включен в целевой версии .NET framework проекта.

## <a name="rule-description"></a>Описание правила
 Новые элементы и типы были включены в .NET Framework 2.0 с пакетом обновления 1 и 2, .NET Framework 3.0 с пакетом обновления 1 и 2 и .NET Framework 3.5 с пакетом обновления 1. Проекты, предназначенные для основных версий платформы .NET Framework, могут непреднамеренно иметь зависимости от этих новых интерфейсов API. Чтобы предотвратить эту зависимость, это правило срабатывает при обнаружении новых членов и типов, которые не были включены по умолчанию с целевой платформой проекта.

 **Целевая рабочая среда и зависимостей пакета службы**

|||
|-|-|
|Целевая платформа|Активируется при обнаружении членов, появившихся в|
|.NET Framework 2.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET framework 2.0 SP1, SP2 .NET Framework 2.0, .NET Framework 3.0 с пакетом обновления 1, .NET Framework 3.0 с пакетом обновления 2|
|.NET Framework 3,5|.NET Framework 3.5 SP1|
|.NET Framework 4|Н/Д|

 Для изменения целевой платформы проекта см. в разделе [как: Определение целевой версии .NET](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы удалить зависимость от пакета обновления, удалите все случаи использования нового члена или типа. Если это зависимость добавлена специально отключить предупреждение, или отключить это правило.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если это не было намеренным зависимость от указанного пакета обновления. В этом случае приложение может не работать на системах, не установлен пакет обновления. Вывод предупреждений или отключить это правило, если это была зависимость добавлена специально.

## <a name="example"></a>Пример
 В следующем примере класс, который использует тип DateTimeOffset, доступна только в пакете обновления 1 для .NET 2.0. В этом примере требуется, что .NET Framework 2.0 был выбран в раскрывающемся списке требуемой версии .NET Framework в свойствах проекта.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Пример
 В следующем примере устраняется нарушение, описанное выше, заменив случаи использования типа DateTimeOffset с типом DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>См. также

- [Portability Warnings](../code-quality/portability-warnings.md)
- [Framework, предназначенных для обзора](../ide/visual-studio-multi-targeting-overview.md)