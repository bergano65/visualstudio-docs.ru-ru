---
title: "CA1903: использовать API-интерфейс только из целевой исполняющей среды | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1903: использовать API-интерфейс только из целевой исполняющей среды
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Категория|Microsoft.Portability|  
|Критическое изменение|Критическое — если нарушение происходит при соответствии сигнатуре видимого для внешнего кода члена или типа.<br /><br /> Некритическое — если нарушение происходит в теле метода.|  
  
## Причина  
 Член или тип использует член или тип, который был впервые представлен в пакете обновления, не включенном в целевую среду проекта.  
  
## Описание правила  
 В .NET Framework 2.0 с пакетами обновлений 1 и 2, .NET Framework 3.0 с пакетами обновлений 1 и 2, а также в .NET Framework 3.5 с пакетом обновлений 1 были включены новые члены и типы.  Проекты, предназначенные для основных версий платформы .NET Framework, могут непреднамеренно иметь зависимости от этих новых API.  Чтобы предотвратить возникновения таких зависимостей, данное правило выполняется при обнаружении новых членов и типов, которые по умолчанию не входят в целевую среду проекта.  
  
 **Зависимости целевой платформы и пакета обновления**  
  
|||  
|-|-|  
|Целевая платформа|Правило выполняется при обнаружении членов, введенных в|  
|.NET Framework 2.0|Платформа .NET Framework 2.0 с пакетом обновления 1 \(SP1\), платформа .NET Framework 2.0 с пакетом обновления 2 \(SP2\)|  
|.NET Framework 3.0|Платформа .NET Framework 2.0 с пакетом обновления 1 \(SP1\), платформа .NET Framework 2.0 с пакетом обновления 2 \(SP2\), платформа .NET Framework 3.0 с пакетом обновления 1 \(SP1\), платформа .NET Framework 3.0 с пакетом обновления 2 \(SP2\)|  
|.NET Framework 3.5|.NET Framework 3.5 с пакетом обновления 1 \(SP1\)|  
|.NET Framework 4|Недоступно|  
  
 Дополнительные сведения об изменении целевой платформы проекта см. в разделе [Настройка конкретной версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## Устранение нарушений  
 Чтобы удалить зависимость от пакета обновления, устраните все случаи использования нового члена или типа.  Если зависимость добавлена специально, отключите вывод предупреждений или само правило.  
  
## Отключение предупреждений  
 Не отключайте предупреждения этого правила, если зависимость от указанного пакета обновления не была добавлена намеренно.  В этом случае приложение может не работать в системах, в которых не установлен необходимый пакет обновления.  Если зависимость добавлена специально, отключите вывод предупреждений или само правило.  
  
## Пример  
 В следующем примере показан класс, который использует тип DateTimeOffset, доступный только в .NET 2.0 с пакетом обновления 1 \(SP1\).  В этом примере необходимо выбрать в раскрывающемся списке требуемых версий .NET Framework окна свойств проекта версию .NET Framework 2.0.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## Пример  
 В следующем примере нарушение, описанное выше, устраняется посредством добавления замены типа DateTimeOffset типом DateTime.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## См. также  
 [Предупреждения переносимости](../code-quality/portability-warnings.md)   
 [Настройка конкретной версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)