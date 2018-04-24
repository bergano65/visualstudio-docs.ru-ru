---
title: 'CA2200: следует повторно вызывать исключение для сохранения сведений о стеке'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c43ba2e9f87d19111ceb43708780c0dd2e9e7e39
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: следует повторно вызывать исключение для сохранения сведений о стеке
|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Исключение вызывается повторно и явным образом задается исключение в `throw` инструкции.

## <a name="rule-description"></a>Описание правила
 Исключение, часть сведений, содержащихся в нем после трассировку стека. Трассировка стека является список иерархий вызовов методов, который начинается с методом, который создает исключение и заканчивается методом, который перехватывает исключение. Если создано исключение повторно, указав на исключение `throw` инструкции будет перезапущена трассировку стека текущего метода и список вызовов метода между исходным методом, создавшим исключение и текущим методом будет утерян. Чтобы сохранить исходные сведения о трассировке стека с исключением, используйте `throw` инструкции без указания исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, повторно создайте исключение без явного указания исключения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан метод, `CatchAndRethrowExplicitly`, который нарушает правила и метод, `CatchAndRethrowImplicitly`, которой соответствует правило.

 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]