---
title: "CA1406: не следует использовать аргументы Int64 для клиентов Visual Basic 6 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406: не следует использовать аргументы Int64 для клиентов Visual Basic 6
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип, который специально помечен как видимый для COM, объявляет член, который принимает аргумент типа <xref:System.Int64?displayProperty=fullName>.  
  
## Описание правила  
 COM\-клиенты VisualBasic 6 не могут получать доступ к 64\-разрядным целым числам.  
  
 По умолчанию для модели COM видимы следующие объекты: сборки, общие типы, члены общих экземпляров в общих типах и все элементы общих типов значений.  Однако чтобы снизить количество ложных положительных результатов, данное правило требует явно указывать видимость типа для COM; содержащая тип сборка должна быть помечена атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>, для которого установлено значение `false`, а тип необходимо пометить атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> со значением `true`.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила для параметра, значение которого всегда можно представить 32\-разрядным целым числом, измените тип параметра на <xref:System.Int32?displayProperty=fullName>.  Если значение параметра слишком велико для представления в виде 32\-разрядного целого числа, измените тип параметра на <xref:System.Decimal?displayProperty=fullName>.  Обратите внимание, что при преобразовании в тип <xref:System.Single?displayProperty=fullName> или <xref:System.Double?displayProperty=fullName> происходит потеря точности в области верхней границы диапазона допустимых значений типа <xref:System.Int64>.  Если член не предназначен для взаимодействия с COM, пометьте его атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> со значением `false`.  
  
## Отключение предупреждений  
 Отключение предупреждений данного правила безопасно в том случае, если COM\-клиенты Visual Basic 6 не получают доступ к типу.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## Связанные правила  
 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: не используйте статические члены в видимых COM типах](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## См. также  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Тип данных Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)