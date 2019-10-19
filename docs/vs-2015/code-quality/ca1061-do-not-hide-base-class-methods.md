---
title: 'CA1061: не скрывать методы базового класса | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 24579e6aa3ba1bf70ed6f195091152b60f3232a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604016"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: не следует скрывать методы базового класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Производный тип объявляет метод с тем же именем и с тем же количеством параметров, что и один из его базовых методов. один или несколько параметров являются базовым типом соответствующего параметра в базовом методе. и все остальные параметры имеют типы, идентичные соответствующим параметрам в базовом методе.

## <a name="rule-description"></a>Описание правила
 Метод в базовом типе скрыт с помощью метода с идентичным именем в производном типе, когда сигнатура параметра производного метода отличается только типами, которые являются более слабыми, чем соответствующие типы в сигнатуре параметра базового метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите или переименуйте метод или измените сигнатуру параметра таким образом, чтобы метод не скрывал базовый метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан метод, нарушающий правило.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]
