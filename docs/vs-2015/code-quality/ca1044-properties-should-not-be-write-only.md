---
title: CA1044. Свойства не должны быть доступны только для записи | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 444081d1e55bd76b67162add508d4f78415e4b3b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143197"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044. Свойства не должны быть доступными только для записи
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Общедоступное или защищенное свойство имеет метод доступа set, но не имеет метода доступа get.

## <a name="rule-description"></a>Описание правила
 Получите методы доступа предоставляют доступ на чтение к свойству и методы доступа set предоставляют доступ на запись. Несмотря на то, что допустимо, а часто и необходимо иметь свойство, доступное только на чтение, рекомендации по разработке запрещают использование свойств, доступных только на запись. Это так, как позволить пользователю задать значение и затем запретить пользователю просмотр значения не поддерживает все параметры безопасности. Кроме того, при отсутствии доступа на чтение нельзя просмотреть состояние общих объектов, что снижает их полезность.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте метод доступа get свойства. Кроме того при необходимости поведение свойства только для записи, можно преобразовать это свойство в метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Настоятельно рекомендуется не отключайте предупреждение из этого правила.

## <a name="example"></a>Пример
 В следующем примере `BadClassWithWriteOnlyProperty` является типом со свойством только для записи. `GoodClassWithReadWriteProperty` содержит Исправленный код.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
