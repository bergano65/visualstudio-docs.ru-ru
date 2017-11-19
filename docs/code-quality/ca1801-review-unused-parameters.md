---
title: "CA1801: Проверьте неиспользуемые параметры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bb8c38d1436ca687664f92bfe0ba6db1ccf68ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: проверьте неиспользуемые параметры
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое, если элемент не отображается за пределами сборки, независимо от того, сделанные изменения.<br /><br /> Не критическое, если изменить элемент с помощью параметра в его теле.<br /><br /> Критическое, если параметр будет удален, и она отображается за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Сигнатура метода включает параметр, не использующийся в основной части метода. Это правило не проверяет следующие методы:  
  
-   Методы, на который указывает делегат.  
  
-   Методы, используемые в качестве обработчиков событий.  
  
-   Методы объявлены с `abstract` (`MustOverride` в Visual Basic) модификатор.  
  
-   Методы объявлены с `virtual` (`Overridable` в Visual Basic) модификатор.  
  
-   Методы объявлены с `override` (`Overrides` в Visual Basic) модификатор.  
  
-   Методы объявлены с `extern` (`Declare` инструкции на языке Visual Basic) модификатор.  
  
## <a name="rule-description"></a>Описание правила  
 Проверьте параметры в невиртуальных методов, которые не используются в теле метода, чтобы убедиться в том, что код не содержит ошибок, для доступа к ним. Неиспользуемые параметры влекут затраты на обслуживание и производительности.  
  
 Иногда нарушение этого правила может указывать на ошибку в метод реализации. Например параметр должен использовались в теле метода. Отключение предупреждений данного правила, если параметр должен существовать из-за обратной совместимости.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите неиспользуемый параметр (критическое изменение) или используйте параметр в теле метода (некритическое изменение).  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила для поставленного ранее кода, для которого будет критическим изменением.  
  
## <a name="example"></a>Пример  
 В следующем примере показано два метода. Один метод нарушает правило, а другой метод, соответствующий этому правилу.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)