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
ms.openlocfilehash: e9746119c746679817076c86e3d5a9080cec30d9
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744687"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031. Не перехватывайте типы общих исключений

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Общие исключения, такие как <xref:System.Exception?displayProperty=fullName> или <xref:System.SystemException?displayProperty=fullName> перехватывается в `catch` инструкции или универсальной конструкции catch например `catch()` используется.

## <a name="rule-description"></a>Описание правила
 Общие исключения не должны перехватываться.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, перехватить исключение более конкретного характера или повторно выдать общее исключение в последнем операторе в `catch` блока.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Перехват типы общих исключений может скрыть проблемы времени выполнения от пользователя библиотеки и может сделать отладку намного сложнее.

> [!NOTE]
> Начиная с .NET Framework 4, среда CLR (CLR) больше не предоставляет исключения поврежденного состояния, которые происходят в операционную систему и управляемого кода, например нарушения прав доступа в [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], для обработки в управляемом коде. Если вы хотите компиляции приложения в .NET Framework 4 или более поздней версии и поддерживать обработку исключений поврежденного состояния, вы можете применить <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут к методу, который обрабатывает исключения поврежденного состояния.

## <a name="example"></a>Пример
 В следующем примере показано, тип, который нарушает это правило и тип, реализующий правильно `catch` блока.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2200: Исключение для сохранения сведений о стеке](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)