---
title: "CA1058: Типы не должны расширять определенные базовые типы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45cddd908c53d129a230b998c6dad03196a31c49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: типы не должны расширять определенные базовые типы
|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Видимый извне тип расширяет некоторые базовые типы. В настоящее время это правило выдает сообщение типов, производных от следующих типов:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## <a name="rule-description"></a>Описание правила  
 Для [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] рекомендовалось версии 1 для формирования нового исключения из <xref:System.ApplicationException>. Рекомендация был изменен и новые исключения должен быть производным от <xref:System.Exception?displayProperty=fullName> или одного из его подклассов в <xref:System> пространства имен.  
  
 Не следует создавать подкласс <xref:System.Xml.XmlDocument> требуется создать XML-представление базового источника данных или модели объекта.  
  
### <a name="non-generic-collections"></a>Неуниверсальные коллекции  
 Используйте и Расширяйте универсальные коллекции, когда это возможно. Если ранее поставляется неуниверсальных коллекций в коде, не распространяются.  
  
 **Примеры неверного использования**  
  
```csharp  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Примеры правильного использования**  
  
```csharp  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, наследование типа от другого базового типа или универсальной коллекции.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила нарушений о <xref:System.ApplicationException>. Можно безопасно подавить предупреждение из этого правила нарушений о <xref:System.Xml.XmlDocument>. Можно безопасно подавить предупреждение о неуниверсальной коллекции, если код был выпущен ранее.