---
title: CA1031. Не перехватывайте типы общих исключений
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236069"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031. Не перехватывайте типы общих исключений

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
В `catch` операторе перехватывается <xref:System.SystemException?displayProperty=fullName> общее исключение, такое как <xref:System.Exception?displayProperty=fullName> или, или используется общее предложение catch, `catch()` такое как.

## <a name="rule-description"></a>Описание правила
Общие исключения не должны перехватываться.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, перехватите более конкретное исключение или создайте общее исключение в качестве последней инструкции в `catch` блоке.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует. Перехват общих типов исключений может скрывать проблемы времени выполнения от пользователя библиотеки и может усложнить отладку.

> [!NOTE]
> Начиная с .NET Framework 4, общеязыковая среда выполнения (CLR) больше не доставляет исключения поврежденного состояния, которые происходят в операционной системе и управляемом коде, например нарушения [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]прав доступа в, для обработки управляемым кодом. Если требуется скомпилировать приложение в .NET Framework 4 или более поздней версии и поддерживать обработку исключений поврежденного состояния, можно применить <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут к методу, обрабатывающему исключение поврежденного состояния.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий это правило, и тип, который правильно реализует `catch` блок.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA2200: Повторный вызов для сохранения сведений о стеке](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)