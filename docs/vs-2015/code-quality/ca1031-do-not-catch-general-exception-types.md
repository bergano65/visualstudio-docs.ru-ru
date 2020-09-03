---
title: 'CA1031: не перехватывайте типы общих исключений | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542406"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031. Не перехватывайте типы общих исключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В <xref:System.Exception?displayProperty=fullName> <xref:System.SystemException?displayProperty=fullName> операторе перехватывается общее исключение, такое как или `catch` , или используется общее предложение catch, такое как `catch()` .

## <a name="rule-description"></a>Описание правила
 Общие исключения не должны перехватываться.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, перехватите более конкретное исключение или создайте общее исключение в качестве последней инструкции в `catch` блоке.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Перехват общих типов исключений может скрывать проблемы времени выполнения от пользователя библиотеки и может усложнить отладку.

> [!NOTE]
> Начиная с [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] , общеязыковая среда выполнения (CLR) больше не доставляет исключения поврежденного состояния, которые возникают в операционной системе, и управляемый код, например нарушения прав доступа в [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] , для обработки управляемым кодом. Если вы хотите скомпилировать приложение в [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] или более поздних версиях и поддерживать обработку исключений поврежденного состояния, можно применить <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут к методу, обрабатывающему исключение поврежденного состояния.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило, и тип, который правильно реализует `catch` блок.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2200. Повторно порождайте исключения для сохранения сведений стека](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
