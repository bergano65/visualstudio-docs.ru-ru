---
title: "CA1711: идентификаторы не должны иметь неверных суффиксов | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711: идентификаторы не должны иметь неверных суффиксов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Идентификатор имеет неверный суффикс.  
  
## Описание правила  
 В соответствии с соглашением об именовании, определенные зарезервированные суффиксы должны добавляться только к именам типов, которые расширяют некоторые базовые типы или реализуют определенные интерфейсы, а также производных от них типов.  В именах других типов зарезервированные суффиксы использоваться не должны.  
  
 В следующей таблице перечислены зарезервированные суффиксы и связанные с ними базовые типы и интерфейсы.  
  
|Суффикс|Базовый тип или интерфейс|  
|-------------|-------------------------------|  
|Атрибут|<xref:System.Attribute?displayProperty=fullName>|  
|Коллекция|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Делегат обработчика событий.|  
|Исключение|<xref:System.Exception?displayProperty=fullName>|  
|Разрешение|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Стек|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Поток|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Кроме того, **запрещается** использовать следующие суффиксы.  
  
-   Делегат  
  
-   Enum  
  
-   Impl — используйте вместо него суффикс "Core"  
  
-   Ex или подобный суффикс для отличия от прежней версии того же типа  
  
 Соглашения об именах обеспечивают единообразие библиотек, предназначенных для выполнения в среде CLR.  Это позволяет сократить время обучения, необходимое для освоения новых библиотек программного обеспечения, и укрепить уверенность клиента в том, что библиотека была разработана опытным разработчиком управляемого кода.  
  
## Устранение нарушений  
 Удалите суффикс из имени типа.  
  
## Отключение предупреждений  
 Нельзя отключить предупреждение из этого правила, если суффикс не будет однозначен в домене приложения.  
  
## Связанные правила  
 [CA1710: идентификаторы должны иметь правильные суффиксы](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)  
  
## См. также  
 [Атрибуты](../Topic/Attributes1.md)   
 [События и делегаты](http://msdn.microsoft.com/ru-ru/d98fd58b-fa4f-4598-8378-addf4355a115)