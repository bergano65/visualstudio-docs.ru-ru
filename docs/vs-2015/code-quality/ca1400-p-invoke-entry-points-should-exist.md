---
title: ': CA1400 точек входа P / Invoke | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: f564f130c4f225d62b71778bc141170ea528d4ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49810637"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: необходимо наличие точек входа P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



