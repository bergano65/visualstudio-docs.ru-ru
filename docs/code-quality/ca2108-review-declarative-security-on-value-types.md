---
title: 'CA2108: проверьте объявляемые параметры безопасности типов значений'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d07245724d70b5bc6ba69deae4311dcb2a10056
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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

 **Структура пользовательского конструктора: не удалось выполнить запрос. ** 
 **Новые значения SecuredTypeStructure 100 100**
**новые значения SecuredTypeStructure 200 200**
## <a name="see-also"></a>См. также
 [Требования связывания](/dotnet/framework/misc/link-demands) [данных и моделирование](/dotnet/framework/data/index)