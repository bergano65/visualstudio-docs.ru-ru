---
title: 'CA2101: Укажите тип маршалинга для строковых аргументов P-Invoke'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8171c318d419edc49410c44d381e82f088014082
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: укажите тип маршалинга для строковых аргументов P/Invoke
|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Неуправляемого член позволяет частично доверенным вызывающим объектам, содержит строковый параметр и не явного маршалинга этой строки.

## <a name="rule-description"></a>Описание правила
 При преобразовании из Юникода в ANSI, существует возможность, что не все символы Юникода могут использоваться в конкретной кодовой страницы ANSI. *Наилучшее сопоставление* пытается решить эту проблему, подстановка знака для символа, который не может быть представлен. Использование этой функции может привести к уязвимости системы безопасности, поскольку не удается управлять символ, который выбран. Например, вредоносный код может преднамеренно создать строку Юникода, содержащий символы, которые не представлены в конкретной кодовой страницы, которые преобразуются в служебные знаки файловой системы, такие как ".." или «/». Обратите внимание, что проверок безопасности для специальных символов часто происходят прежде, чем строка преобразуется в формат ANSI.

 Наилучшее сопоставление используется по умолчанию для неуправляемых преобразования типа WChar в МБ. Если вы явно отключить наилучшего соответствия, ваш код может содержать уязвимые места, из-за этой проблемы.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, явного маршалинга строковых данных.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано метод, который нарушает это правило, а затем показано, как исправить нарушение.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]