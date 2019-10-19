---
title: 'CA2108: Проверка декларативной безопасности для типов значений | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a05b7098d75d368f893b2504f7663675611bc0ce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658726"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: проверьте объявляемые параметры безопасности типов значений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип значения защищен с помощью запросов [данных и моделирования](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) или [связей](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Описание правила
 Типы значений выделяются и инициализируются по конструкторам по умолчанию перед выполнением других конструкторов. Если тип значения защищен требованием или LinkDemand и вызывающий объект не имеет разрешений, которые соответствуют проверке безопасности, то любой конструктор, отличный от значения по умолчанию, завершится ошибкой, и будет вызвано исключение безопасности. Тип значения не освобождается; он остается в состоянии, заданном по умолчанию конструктором. Не следует рассчитывать на то, что вызывающий объект, передающий экземпляр типа значения, имеет разрешение на создание экземпляра или доступ к нему.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Нарушение этого правила невозможно устранить, если не удалить проверку безопасности из типа и использовать проверку безопасности на уровне метода. Обратите внимание, что устранение нарушения таким образом не помешает вызывающим объектам с недостаточными разрешениями получать экземпляры типа значения. Необходимо убедиться, что экземпляр типа значения, в его состоянии по умолчанию, не раскрывает конфиденциальную информацию и не может использоваться каким-либо опасным способом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если любой вызывающий объект может получить экземпляры типа значения в своем состоянии по умолчанию без угрозы безопасности.

## <a name="example"></a>Пример
 В следующем примере показана библиотека, содержащая тип значения, нарушающего это правило. Обратите внимание, что тип `StructureManager` предполагает, что вызывающий объект, передающий экземпляр типа значения, имеет разрешение на создание экземпляра или доступ к нему.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении демонстрируется слабость библиотеки.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 В этом примере формируются следующие данные:

 **Пользовательский конструктор структуры: запрос не выполнен.** 
**новые значения секуредтипеструктуре 100 100** 
**новые значения секуредтипеструктуре 200 200**
## <a name="see-also"></a>См. также раздел
 [Данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [запросов на связывание](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
