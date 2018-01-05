---
title: ": Ca2200 следует для сохранения сведений стека | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 81dff0b9e876719fdfd26409772498390344cd2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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