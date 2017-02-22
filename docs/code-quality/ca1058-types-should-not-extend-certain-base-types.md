---
title: "CA1058: типы не должны расширять определенные базовые типы | Microsoft Docs"
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
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1058: типы не должны расширять определенные базовые типы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Видимый извне тип расширяет некоторые базовые типы.  В настоящее время это правило относится к типам, производным от следующих типов:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## Описание правила  
 В [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] версии 1 было рекомендовано делать новые производными от <xref:System.ApplicationException>.  Рекомендация изменилась; новые исключения должны быть производными от <xref:System.Exception?displayProperty=fullName> или от одного из его подклассов в пространстве имен <xref:System>.  
  
 Не следует создавать подкласс <xref:System.Xml.XmlDocument>, если нужно создать XML\-представление нижележащей объектной модели или источника данных.  
  
### Неуниверсальные коллекции  
 Используйте и расширяйте универсальные коллекции всегда, когда это возможно.  Не расширяйте неуниверсальные коллекции в коде, за исключением случаев, когда такой код уже был поставлен заказчику ранее.  
  
 **Примеры неверного использования**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Примеры правильного использования**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, сделайте тип производным от другого базового типа или универсальной коллекции.  
  
## Отключение предупреждений  
 Не следует отключать вывод предупреждений для этого правила, если нарушения касаются <xref:System.ApplicationException>.  Можно отключить вывод предупреждений для нарушений, касающихся <xref:System.Xml.XmlDocument>.  Если код был ранее выпущен, можно отключать предупреждения, касающиеся неуниверсальных коллекций.