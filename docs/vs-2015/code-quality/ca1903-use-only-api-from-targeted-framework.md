---
title: 'CA1903: Используйте API только из целевой платформы | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10649b4106a280089fd6b086167c7e92bff1300b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545253"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903. Используйте API только из целевой рабочей среды
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1903: использование API только из целевой платформы](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|Элемент|Значение|
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Категория|Microsoft. переносимость|
|Критическое изменение|Критическое — при срабатывании сигнатуры видимого извне члена или типа.<br /><br /> Не критическое — при срабатывании в теле метода.|

## <a name="cause"></a>Причина
 Элемент или тип использует член или тип, который появился в пакете обновления, который не был включен в целевую платформу проекта.

## <a name="rule-description"></a>Описание правила
 Новые члены и типы были добавлены в .NET Framework 2,0 с пакетом обновления 1 (SP1) и 2, .NET Framework 3,0 с пакетом обновления 1 и 2 и .NET Framework 3,5 с пакетом обновления 1 (SP1). Проекты, предназначенные для основных версий .NET Framework, могут непреднамеренно принимать зависимости от этих новых API. Чтобы предотвратить эту зависимость, это правило срабатывает при использовании любых новых элементов и типов, которые не были включены по умолчанию в целевой платформе проекта.

 **Зависимости целевой платформы и пакета обновления**

|Элемент|Значение|
|-|-|
|Когда Целевая платформа|Срабатывает при использовании членов, появившихся в|
|.NET Framework 2.0|.NET Framework 2,0 с пакетом обновления 1 (SP1), .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|Н/Д|

 Чтобы изменить целевую платформу проекта, см. раздел [нацеленность на определенную версию .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы удалить зависимость от пакета обновления, удалите все случаи использования нового члена или типа. Если эта зависимость заменяется намеренно, отключите предупреждение или выключите это правило.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если это не является преднамеренной зависимостью от указанного пакета обновления. В этом случае приложение может не запуститься в системах без установленного пакета обновления. Подавление предупреждения или отключение этого правила, если это была преднамеренная зависимость.

## <a name="example"></a>Пример
 В следующем примере показан класс, который использует тип DateTimeOffset, доступный только в пакете обновления 1 (SP1) для .NET 2,0. В этом примере требуется, чтобы .NET Framework 2,0 был выбран в раскрывающемся списке Целевая платформа в свойствах проекта.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Пример
 В следующем примере исправляется ранее описанное нарушение путем замены использования типа DateTimeOffset типом DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>См. также
 [Предупреждения переносимости](../code-quality/portability-warnings.md) [, нацеленные на определенную версию .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
