---
title: CA2108. Проверьте объявляемые параметры безопасности типов значений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f6a17bf57f00923cfd31bd477f211ba66169672a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687366"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108. Проверьте объявляемые параметры безопасности типов значений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип значения защищен [данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) или [требования связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Описание правила
 Типы значений выделенных и инициализировать с конструкторы по умолчанию до выполнения других конструкторов. Если тип значения защищен Demand или LinkDemand и вызывающий объект не имеет разрешений, которые не удовлетворяют проверки безопасности, какому-либо конструктору по умолчанию не удастся и будет выдано исключение безопасности. Тип значения не освобождается; он остается в состоянии, задайте его конструктором по умолчанию. Не следует предполагать, что вызывающий объект, который передает экземпляр типа значения имеет разрешение на создание или доступ к экземпляру.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Невозможно устранить нарушение этого правила, если не удалить проверку безопасности на основе типа и проверки безопасности на уровне метода используйте вместо него. Обратите внимание на то, что устранения нарушения таким образом не помешает вызывающие объекты с соответствующими разрешениями, получать экземпляры типа значения. Необходимо убедиться, что экземпляр типа значения, в состоянии по умолчанию, не содержит конфиденциальную информацию и нельзя использовать в злонамеренных целях.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно подавить предупреждение из этого правила, если любой вызывающий объект может получить экземпляры типа значения в состоянии по умолчанию без создания угроз безопасности.

## <a name="example"></a>Пример
 В следующем примере показано это библиотека, содержащая тип значения, который нарушает это правило. Обратите внимание, что `StructureManager` тип предполагает, что вызывающий объект, который передает экземпляр типа значения имеет разрешение на создание или доступ к экземпляру.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении демонстрируется уязвимость библиотеки.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 В этом примере формируются следующие данные:

 **Структура пользовательского конструктора: Не удалось выполнить запрос. ** 
 **Новые значения SecuredTypeStructure 100 100**
**новые значения SecuredTypeStructure 200 200**
## <a name="see-also"></a>См. также
 [Требования связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
