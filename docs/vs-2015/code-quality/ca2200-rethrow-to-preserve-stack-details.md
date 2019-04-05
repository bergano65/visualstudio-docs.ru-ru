---
title: CA2200. Rethrow для сохранения сведений стека | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed2dd2884268511ae05ac89c132f73fdf8b2771e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992231"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200. Повторно порождайте исключения для сохранения сведений стека
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Исключение выдается заново, и явным образом задается исключение в `throw` инструкции.

## <a name="rule-description"></a>Описание правила
 Когда создается исключение, часть сведений, содержащихся в нем показана трассировка стека. Трассировка стека приведен список иерархии вызовов метода, который начинается с методом, который создает исключение и заканчивается на метод, который перехватывает исключение. Если создано исключение повторно, указав исключение в `throw` инструкции, трассировка стека перезапускается в текущего метода и список вызовов метода между исходным методом, создавшим исключение и текущим методом будет утерян. Чтобы сохранить исходные сведения о трассировке стека с исключением, используйте `throw` инструкции без указания исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, заново создайте исключение без явного указания исключения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан метод `CatchAndRethrowExplicitly`, который нарушает правило и метод, `CatchAndRethrowImplicitly`, которой соблюдается правило.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
