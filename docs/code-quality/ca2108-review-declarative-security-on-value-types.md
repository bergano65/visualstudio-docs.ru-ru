---
title: "CA2108: Проверьте объявляемые параметры безопасности типов значений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a2d7ecd899b4da51e6ff200f1e18b00366db6669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: проверьте объявляемые параметры безопасности типов значений
|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип значения защищен средствами [данных и моделирование](/dotnet/framework/data/index) или [требования связывания](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Описание правила  
 Типы значений выделенных и инициализированную конструкторы по умолчанию до выполнения других конструкторов. Если тип значения защищен проверкой Demand или LinkDemand и вызывающий объект не имеет разрешений, которые удовлетворяют проверки безопасности любого конструктора, отличного от по умолчанию завершится ошибкой и будет создано исключение безопасности. Тип значения не освобождается; она останется в состоянии, установленном его конструктором по умолчанию. Не следует предполагать, что вызывающий объект, который передает экземпляр типа значения имеет разрешение на создание или доступа к экземпляру.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Не удается исправить нарушение этого правила, если не удалить проверку безопасности на основе типа и проверки безопасности на уровне метода используйте вместо него. Обратите внимание, что устранения нарушения таким образом не будет препятствовать вызывающим объектам с соответствующими разрешениями, получать экземпляры типа значения. Необходимо убедиться, не передают важные сведения экземпляр типа значения в состоянии по умолчанию и не может использоваться в злонамеренных целях.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно подавить предупреждение из этого правила, если любой вызывающий объект может получать экземпляры типа значения в состоянии по умолчанию без создания угроз безопасности.  
  
## <a name="example"></a>Пример  
 В следующем примере показано это библиотека, содержащая тип значения, которое нарушает это правило. Обратите внимание, что `StructureManager` тип предполагается, что вызывающий объект, который передает экземпляр типа значения, имеет разрешение на создание или доступа к экземпляру.  
  
 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем приложении демонстрируется уязвимость библиотеки.  
  
 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **Структура пользовательского конструктора: не удалось выполнить запрос.**  
**Новые значения SecuredTypeStructure 100 100**  
**Новые значения SecuredTypeStructure 200 200**   
## <a name="see-also"></a>См. также  
 [Требования связывания](/dotnet/framework/misc/link-demands)   
 [Данные и моделирование](/dotnet/framework/data/index)