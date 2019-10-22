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
ms.openlocfilehash: 2696446ee2b257b78559909c0cba672cded39943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661897"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: не перехватывайте типы общих исключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В инструкции `catch` перехватывается общее исключение, например <xref:System.Exception?displayProperty=fullName> или <xref:System.SystemException?displayProperty=fullName>, или используется общее предложение catch, такое как `catch()`.

## <a name="rule-description"></a>Описание правила
 Общие исключения не должны перехватываться.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, перехватите более конкретное исключение или повторно создайте общее исключение в качестве последней инструкции в блоке `catch`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Перехват общих типов исключений может скрывать проблемы времени выполнения от пользователя библиотеки и может усложнить отладку.

> [!NOTE]
> Начиная с [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] среда CLR больше не доставляет исключения поврежденного состояния, которые происходят в операционной системе и управляемом коде, например нарушения прав доступа в [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], для обработки управляемым кодом. Если требуется скомпилировать приложение в [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] или более поздних версиях и поддерживать обработку исключений поврежденного состояния, можно применить атрибут <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> к методу, обрабатывающему исключение поврежденного состояния.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило, и тип, который правильно реализует блок `catch`.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2200: следует повторно вызывать исключение для сохранения сведений о стеке](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
