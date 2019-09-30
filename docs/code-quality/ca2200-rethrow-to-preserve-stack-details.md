---
title: CA2200. Повторно порождайте исключения для сохранения сведений стека
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5cf7fc6e31b9250392fc3ea447a5b91225640a50
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231910"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200. Повторно порождайте исключения для сохранения сведений стека

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Возникает повторное исключение, и в `throw` инструкции явно указывается исключение.

## <a name="rule-description"></a>Описание правила

После возникновения исключения часть информации, которую он передает, является трассировкой стека. Трассировка стека — это список иерархии вызовов методов, который начинается с метода, который создает исключение и завершается методом, который перехватывает исключение. Если исключение создается повторно путем указания исключения в `throw` инструкции, трассировка стека перезапускается в текущем методе, а список вызовов методов между исходным методом, вызвавшим исключение, и текущим методом теряется. Для сохранения исходных данных трассировки стека с исключением используйте `throw` инструкцию без указания исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, воссоздайте исключение без явного указания исключения.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере показан метод, `CatchAndRethrowExplicitly`который нарушает правило, и `CatchAndRethrowImplicitly`метод, который удовлетворяет правилу.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]