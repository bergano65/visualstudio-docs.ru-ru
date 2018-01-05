---
title: "CA2112: Защищенные типы не должны предоставлять поля | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e3959540d00a74d99095a3facf824d822827a00d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: защищенные типы не должны предоставлять поля
|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип содержит открытые поля и защищен [требования связывания](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Описание правила  
 Если код имеет доступ к экземпляру типа, защищенного запросом компоновки, то для получения доступа к полям типа коду не требуется удовлетворять запросу компоновки.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделать поля неоткрытыми и добавить открытые свойства или методы, возвращающие данные поля. Проверки безопасности LinkDemand для типов защиты доступа к свойствам и методам типа. Тем не менее доступом для кода не применяется к полям.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для проблем безопасности и создать эффективную систему необходимо устранить нарушения, делая nonpublic открытые поля. Можно подавить предупреждение из этого правила, если поле не содержит информации, которую требуется защищать, и не следует полагаться на значения поля.  
  
## <a name="example"></a>Пример  
 Следующий пример состоит из типа библиотеки (`SecuredTypeWithFields`) с незащищенными полями, типа (`Distributor`), можно создать экземпляры типа библиотеки ошибочный передает экземпляров типа нет разрешения для их создания и кода приложения, можно прочитать поля экземпляра, несмотря на то, что он не имеет разрешения, которое защищает тип.  
  
 Следующий код библиотеки нарушает правило.  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## <a name="example"></a>Пример  
 Приложение не может создать экземпляр из-за запрос компоновки защищает тип. Следующий класс позволяет приложению получить экземпляр защищенного типа.  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## <a name="example"></a>Пример  
 В следующем приложении демонстрируется, как это сделать, без разрешения для доступа к методам защищенного типа, код может обращаться к его поля.  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **Создание экземпляра SecuredTypeWithFields.**  
**Защищенные поля типа: 22, 33**  
**Изменение защищенного типа поля...**  
**Поля объекта в кэше: 99, 33**   
## <a name="related-rules"></a>Связанные правила  
 [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>См. также  
 [Требования связывания](/dotnet/framework/misc/link-demands)   
 [Данные и моделирование](/dotnet/framework/data/index)