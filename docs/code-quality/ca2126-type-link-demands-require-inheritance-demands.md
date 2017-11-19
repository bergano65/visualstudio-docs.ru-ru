---
title: "CA2126: Запросы компоновки типа требуют запросы наследования | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 254fd15f97afe69f927bb8a1aae1954105776641
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: запросы компоновки типа требуют запросы наследования
|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|CheckId|CA2126|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый незапечатанный тип защищен требованием ссылки имеет переопределяемый метод, и ни тип, ни метод не защищены требованием наследования.  
  
## <a name="rule-description"></a>Описание правила  
 Запрос компоновки в методе или его объявляющий тип требует немедленного вызывающему объекту метода указанное разрешение. Требование наследования в методе требует метод переопределения для указанного разрешения. Требование наследования в типе требует для указанное разрешение производного класса.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, защитите тип или метод с требованием наследования для те же разрешения, как требование связывания.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2108: проверьте объявляемые параметры безопасности типов значений](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122: не используйте косвенное представление методов с запросами компоновки](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123: запросы компоновки переопределения должны быть идентичны базовым](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## <a name="see-also"></a>См. также  
 [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)   
 [Требования к наследованию](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Требования связывания](/dotnet/framework/misc/link-demands)   
 [Требования](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)