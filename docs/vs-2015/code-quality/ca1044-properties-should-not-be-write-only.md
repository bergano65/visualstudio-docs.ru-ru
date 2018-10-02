---
title: 'CA1044: Свойства не должны быть доступны только на запись | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 732af1dcdeff669723f717dabe035a38640a8bf3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592372"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: свойства не должны быть доступны только на запись
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1044: свойства не должны быть доступны только для записи](https://docs.microsoft.com/visualstudio/code-quality/ca1044-properties-should-not-be-write-only).

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



