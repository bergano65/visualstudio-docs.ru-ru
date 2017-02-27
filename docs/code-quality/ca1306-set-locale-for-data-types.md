---
title: "CA1306: указывайте языковой стандарт для типов данных | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1306: указывайте языковой стандарт для типов данных
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод или конструктор создал один или несколько экземпляров <xref:System.Data.DataTable?displayProperty=fullName> или <xref:System.Data.DataSet?displayProperty=fullName> и не установил явным образом свойство языка \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> или <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\).  
  
## Описание правила  
 Язык и региональные параметры определяют представление элементов данных, таких как формат чисел, обозначение денежных единиц и порядок сортировки.  При создании <xref:System.Data.DataTable> или<xref:System.Data.DataSet> следует указывать язык явным образом.  По умолчанию для этих типов используются текущие языковые и региональные параметры.  Для общедоступных данных, хранящихся в базе данных или в файле, обычно следует указывать инвариантные языковые параметры \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\).  При общем доступе к данным из систем с различными языковыми параметрами применение языковых параметров по умолчанию может привести к тому, что содержимое <xref:System.Data.DataTable> или <xref:System.Data.DataSet> будет неправильно отображено или обработано.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правило, следует явным образом указать языковые параметры для <xref:System.Data.DataTable> и <xref:System.Data.DataSet>.  
  
## Отключение предупреждений  
 Можно безопасно отключать предупреждения этого правила, если библиотека или приложение предназначены для ограниченного круга локальных пользователей, общий доступ к данным не предоставляется, или применение параметров по умолчанию допустимо для всех поддерживаемых скриптов.  
  
## Пример  
 В следующем примере демонстрируется создание двух экземпляров <xref:System.Data.DataTable>.  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## См. также  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>