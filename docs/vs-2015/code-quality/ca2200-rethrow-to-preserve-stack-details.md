---
title: 'CA2200: повторный вызов для сохранения сведений о стеке | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d20407d7cc708ac785e4a792bf8e64768ea58540
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667389"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: следует повторно вызывать исключение для сохранения сведений о стеке
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Создается повторное исключение, и в инструкции `throw` явно указывается исключение.

## <a name="rule-description"></a>Описание правила
 После возникновения исключения часть информации, которую он передает, является трассировкой стека. Трассировка стека — это список иерархии вызовов методов, который начинается с метода, который создает исключение и завершается методом, который перехватывает исключение. Если исключение создается повторно путем указания исключения в операторе `throw`, трассировка стека перезапускается в текущем методе, а список вызовов методов между исходным методом, вызвавшим исключение, и текущим методом теряется. Для сохранения исходных данных трассировки стека с исключением используйте инструкцию `throw` без указания исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, повторно создайте исключение без явного указания исключения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан метод, `CatchAndRethrowExplicitly`, который нарушает правило и метод, `CatchAndRethrowImplicitly`, который соответствует правилу.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
