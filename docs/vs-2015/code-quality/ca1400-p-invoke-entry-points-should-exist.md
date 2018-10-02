---
title: ': CA1400 точек входа P / Invoke | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0544fb21533e3f114ab1efdc315d844b4cad0acb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592305"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: необходимо наличие точек входа P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1400: точек входа P / Invoke должны существовать](https://docs.microsoft.com/visualstudio/code-quality/ca1400-p-invoke-entry-points-should-exist).

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод, помеченный атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке. Если правило не удается найти имя метода, так же, как он указан, он ищет ANSI или Юникода версии метода, добавив к имени метода с 'A' или 'W'. Если совпадений не найдено, правило пытается найти функцию с помощью формата имени __stdcall (_MyMethod@12, где 12 — это длина аргументов). Если совпадений не найдено, и имя метода начинается с «#», выполняется поиск как порядковым номером вместо ссылки на имя функции.

## <a name="rule-description"></a>Описание правила
 Проверка во время компиляции доступен убедитесь, что методы, помеченные атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute> расположены в упоминаемой неуправляемой библиотеки DLL. Если не функцию, которая имеет указанное имя не находится в библиотеке или аргументов для метода аргументы функции не совпадают, среда CLR создает исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, исправьте метод, который имеет <xref:System.Runtime.InteropServices.DllImportAttribute> атрибута. Убедитесь, что неуправляемая библиотека существует и находится в том же каталоге, что и сборка, содержащая метод. Если библиотека еще существует и правильно указана, убедитесь, что имя метода, возвращаемый тип и подпись аргумента соответствуют функции библиотеки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, когда неуправляемая библиотека находится в том же каталоге, что управляемую сборку, которая ссылается на нее. Можно безопасно подавить предупреждение из этого правила в случае, когда неуправляемая библиотека, не удалось найти.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило. Нет функции, которая называется `DoSomethingUnmanaged` происходит в kernel32.dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>



