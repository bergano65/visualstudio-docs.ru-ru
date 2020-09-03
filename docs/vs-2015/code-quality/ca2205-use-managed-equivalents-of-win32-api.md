---
title: 'CA2205: использование управляемых эквивалентов API Win32 | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 85e27ab04ca81f5513a0b09bc41548f4a7c2430d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547684"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205. Используйте управляемые эквиваленты Win32 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Определен метод вызова платформы и метод с эквивалентной функциональностью существует в [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] библиотеке классов.

## <a name="rule-description"></a>Описание правила
 Метод вызова платформы используется для вызова неуправляемой функции DLL и определяется с помощью <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибута или `Declare` ключевого слова в Visual Basic. Неверно определенный метод вызова неуправляемого кода может привести к исключениям среды выполнения из-за таких проблем, как неправильно названная функция, ошибочное сопоставление типов данных параметров и возвращаемых значений и неверные спецификации полей, такие как соглашение о вызовах и кодировка. Если доступно, то обычно проще и меньше ошибок вызывает эквивалентный управляемый метод, чем для определения и непосредственного вызова неуправляемого метода. Вызов метода вызова неуправляемого кода также может привести к дополнительным проблемам безопасности, которые необходимо решить.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените вызов неуправляемой функции вызовом управляемого эквивалента.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если предлагаемый метод замены не предоставляет необходимые функции.

## <a name="example"></a>Пример
 В следующем примере показано определение метода вызова платформы, нарушающее правило. Кроме того, показаны вызовы метода вызова неуправляемого кода и эквивалентного управляемого метода.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1404: вызов GetLastError сразу после P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: перемещение P/Invoke в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: должны существовать точки входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: укажите маршалирование для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
