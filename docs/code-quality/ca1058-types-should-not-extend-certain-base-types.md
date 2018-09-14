---
title: 'CA1058: типы не должны расширять определенные базовые типы'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a18abfa94d3d53c6b96558fdf1cfc8d0c1c9cc5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549710"
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

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 Для [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] рекомендовалось версии 1, для получения новых исключений из <xref:System.ApplicationException>. Изменились рекомендации и новые исключения должен быть производным от <xref:System.Exception?displayProperty=fullName> или одного из его подклассов в <xref:System> пространства имен.

 Не следует создавать подкласс <xref:System.Xml.XmlDocument> Если вы хотите создать XML-представление базового источника данных или модели объекта.

### <a name="non-generic-collections"></a>Неуниверсальные коллекции
 Используйте и Расширяйте универсальные коллекции, когда это возможно. Не была расширена неуниверсальных коллекций в коде, если не поставляется ранее.

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
 Чтобы устранить нарушение этого правила, наследование типа от другого базового типа или универсальной коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила для нарушения о <xref:System.ApplicationException>. Это безопасно подавить предупреждение из этого правила для нарушения о <xref:System.Xml.XmlDocument>. Его можно безопасно подавить предупреждение о неуниверсальной коллекции, если код был выпущен ранее.