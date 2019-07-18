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
ms.openlocfilehash: bb5160ef663375ee3dd4b45797e8f4536acdf793
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66744645"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820. Проверяйте наличие пустых строк, используя длину строки

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Строка сравнивается с пустой строкой, используя <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Описание правила

Сравнение строк с помощью <xref:System.String.Length%2A?displayProperty=nameWithType> свойство или <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> быстрее, чем при использовании <xref:System.Object.Equals%2A>. Это обусловлено <xref:System.Object.Equals%2A> выполняет значительно больше инструкции MSIL, чем любая <xref:System.String.IsNullOrEmpty%2A> или количество выполненных для получения инструкций <xref:System.String.Length%2A> свойство значение и сравнить это значение ноль.

Для строки null <xref:System.Object.Equals%2A> и `<string>.Length == 0` ведут себя по-разному. Если попытаться получить значение <xref:System.String.Length%2A> свойство для строки null, среда CLR создает <xref:System.NullReferenceException?displayProperty=fullName>. Если выполнить сравнение строку null и пустые строки, среда CLR создает исключение и возвращает `false`. Проверка значений null не оказывает существенного влияния относительную производительность этих двух подходов. При нацеливании на .NET Framework 2.0 или более поздней версии, используйте <xref:System.String.IsNullOrEmpty%2A> метод. В противном случае используйте <xref:System.String.Length%2A> == 0 сравнения, когда это возможно.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените выражение, чтобы использовать <xref:System.String.IsNullOrEmpty%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если производительность не является проблемой.

## <a name="example"></a>Пример

В следующем примере показано различные методики, которые используются для поиска пустой строкой.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]