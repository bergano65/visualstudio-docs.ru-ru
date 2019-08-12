---
title: CA1400. Для методов P/Invoke должны существовать точки входа
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b292c58e666c11130fb25f67c234bfd2282fe463
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922259"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400. Для методов P/Invoke должны существовать точки входа

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Открытый или защищенный метод помечается атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке. Если правило не может найти имя метода точно так же, как указано, оно ищет версии метода в кодировке ANSI или расширенных символов, заменяя имя метода на "A" или "W". Если совпадений не найдено, правило пытается найти функцию с помощью формата имени __stdcall (_MyMethod@12, где 12 обозначает длину аргументов). Если совпадений не найдено, а имя метода начинается с символа "#", правило ищет функцию как порядковую ссылку, а не ссылку на имя.

## <a name="rule-description"></a>Описание правила
Проверка на время компиляции недоступна, чтобы методы, помеченные <xref:System.Runtime.InteropServices.DllImportAttribute> , были размещены в неуправляемой библиотеке DLL, на которую указывает ссылка. Если в библиотеке нет функции с указанным именем или аргументы метода не совпадают с аргументами функции, среда CLR выдает исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, исправьте метод с <xref:System.Runtime.InteropServices.DllImportAttribute> атрибутом. Убедитесь, что неуправляемая библиотека существует и находится в том же каталоге, что и сборка, содержащая метод. Если библиотека существует и правильно указана, убедитесь, что имя метода, возвращаемый тип и сигнатура аргумента соответствуют библиотечной функции.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не отключайте предупреждение из этого правила, если неуправляемая библиотека находится в том же каталоге, что и управляемая сборка, которая ссылается на нее. Можно спокойно отключить предупреждение из этого правила в случае, если не удается найти неуправляемую библиотеку.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило. В kernel32. dll не `DoSomethingUnmanaged` выполняется ни одна функция с именем.

[!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>См. также
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>