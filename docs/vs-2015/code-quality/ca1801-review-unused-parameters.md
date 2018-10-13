---
title: 'CA1801: Проверьте неиспользуемые параметры | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0946e315aef0c333207d49eb14820d287a9b361
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269689"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: проверьте неиспользуемые параметры
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [CA1801: Проверьте неиспользуемые параметры](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое, если член не видимый за пределами сборки, независимо от того, сделанные изменения.<br /><br /> Не критическое — при изменении элемента для использования параметра в своем теле.<br /><br /> Критическое, если параметр будет удален, и отображается за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Сигнатура метода включает параметр, не использующийся в основной части метода. Это правило не проверяет следующие методы:  
  
-   Методы ссылается делегат.  
  
-   Методы, используемые в качестве обработчиков событий.  
  
-   Методы, объявленные с `abstract` (`MustOverride` в Visual Basic) модификатор.  
  
-   Методы, объявленные с `virtual` (`Overridable` в Visual Basic) модификатор.  
  
-   Методы, объявленные с `override` (`Overrides` в Visual Basic) модификатор.  
  
-   Методы, объявленные с `extern` (`Declare` в Visual Basic) модификатор.  
  
## <a name="rule-description"></a>Описание правила  
 Проверьте параметры в невиртуальных методов, которые не используются в теле метода, чтобы убедиться в том, что код не содержит ошибок, для доступа к ним. Неиспользуемые параметры влекут затраты на обслуживание и производительность.  
  
 Иногда нарушение этого правила может указывать на ошибку в метод реализации. Например параметр должен использовались в теле метода. Подавлять предупреждения этого правила, если параметр должен существовать из-за обратной совместимости.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, удалить неиспользуемый параметр (критическое изменение) или используйте параметр в теле метода (некритическое изменение).  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила для ранее созданного кода, для которого будет критическим изменением.  
  
## <a name="example"></a>Пример  
 В следующем примере два метода. Один метод нарушает правило, а другой метод, соответствующий этому правилу.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)

