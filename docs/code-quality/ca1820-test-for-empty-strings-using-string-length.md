---
title: CA1820. Проверяйте наличие пустых строк, используя длину строки
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233419"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820. Проверяйте наличие пустых строк, используя длину строки

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Строка сравнивается с пустой строкой с помощью <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Описание правила

Сравнение строк с помощью <xref:System.String.Length%2A?displayProperty=nameWithType> свойства <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> или метода выполняется быстрее, чем при <xref:System.Object.Equals%2A>использовании. Это обусловлено <xref:System.Object.Equals%2A> тем, что выполняет значительно больше инструкций MSIL <xref:System.String.IsNullOrEmpty%2A> , чем или количество выполняемых <xref:System.String.Length%2A> инструкций для получения значения свойства и сравнивает его с нулем.

Для пустых строк <xref:System.Object.Equals%2A> и `<string>.Length == 0` ведет себя по-разному. Если попытаться получить значение <xref:System.String.Length%2A> свойства в строке null, среда CLR <xref:System.NullReferenceException?displayProperty=fullName>выдаст исключение. При выполнении сравнения между пустой строкой и пустой строкой среда CLR не создает исключение и возвращает `false`. Тестирование на значение NULL не оказывает существенного влияния на относительную производительность этих двух подходов. При нацеливании на <xref:System.String.IsNullOrEmpty%2A> .NET Framework 2,0 или более поздней версии используйте метод. В противном случае <xref:System.String.Length%2A> используйте сравнение = = 0 везде, где это возможно.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените сравнение для использования <xref:System.String.IsNullOrEmpty%2A> метода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Вы можете отключить предупреждение из этого правила, если производительность не является проблемой.

## <a name="example"></a>Пример

В следующем примере показаны различные методы, используемые для поиска пустой строки.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]