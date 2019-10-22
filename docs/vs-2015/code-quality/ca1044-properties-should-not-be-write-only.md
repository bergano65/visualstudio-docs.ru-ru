---
title: 'CA1044: свойства не должны быть только для записи | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa2d07337ec48e41a9d8ad82602a387159192f92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668273"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: свойства не должны быть доступны только на запись
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытое или защищенное свойство имеет метод доступа set, но не имеет метода доступа get.

## <a name="rule-description"></a>Описание правила
 Методы доступа get предоставляют доступ для чтения к свойству, а методы доступа set предоставляют доступ на запись. Несмотря на то, что допустимо, а часто и необходимо иметь свойство, доступное только на чтение, рекомендации по разработке запрещают использование свойств, доступных только на запись. Это связано с тем, что предоставление пользователю возможности задать значение и предотвратить его просмотр пользователем не обеспечивает никакой безопасности. Кроме того, при отсутствии доступа на чтение нельзя просмотреть состояние общих объектов, что снижает их полезность.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте метод доступа get к свойству. Кроме того, если требуется поведение свойства только для записи, рассмотрите возможность преобразования этого свойства в метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Настоятельно рекомендуется не отключать предупреждение из этого правила.

## <a name="example"></a>Пример
 В следующем примере `BadClassWithWriteOnlyProperty` является типом с свойством, предназначенным только для записи. `GoodClassWithReadWriteProperty` содержит исправленный код.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
