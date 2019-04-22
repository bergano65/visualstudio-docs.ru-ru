---
title: CA1903. Используйте API-Интерфейс только из целевой версии .NET framework | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 146563dfa358367e7c22f8ad37564b85d64eaf1d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647159"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903. Используйте API только из целевой рабочей среды
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio, см. в разделе [CA1903: Используйте API-Интерфейс только из целевой версии .NET framework](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).  
  
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
  
 Для изменения целевой платформы проекта см. в разделе [предназначенных для определенной версии .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы удалить зависимость от пакета обновления, удалите все случаи использования нового члена или типа. Если это зависимость добавлена специально отключить предупреждение, или отключить это правило.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, если это не было намеренным зависимость от указанного пакета обновления. В этом случае приложение может не работать на системах, не установлен пакет обновления. Вывод предупреждений или отключить это правило, если это была зависимость добавлена специально.  
  
## <a name="example"></a>Пример  
 В следующем примере класс, который использует тип DateTimeOffset, доступна только в пакете обновления 1 для .NET 2.0. В этом примере требуется, что .NET Framework 2.0 был выбран в раскрывающемся списке требуемой версии .NET Framework в свойствах проекта.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>Пример  
 В следующем примере устраняется нарушение, описанное выше, заменив случаи использования типа DateTimeOffset с типом DateTime.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>См. также  
 [Предупреждения переносимости](../code-quality/portability-warnings.md)   
 [Настройка конкретной версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
