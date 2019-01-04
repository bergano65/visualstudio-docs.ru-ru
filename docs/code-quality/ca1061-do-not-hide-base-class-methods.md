---
title: CA1061. Не скрывайте методы базовых классов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0a6db369cea0e242ce5b2b6e169278b1bf17ea2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928559"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061. Не скрывайте методы базовых классов

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Производный тип объявляет метод, с тем же именем и одинаковое число параметров, как один из базовых методов; один или несколько параметров, — это базовый тип соответствующего параметра в метод базового; и остальные параметры имеют типы, которые совпадают с соответствующими параметрами в базовый метод.

## <a name="rule-description"></a>Описание правила
 Метод в базовом типе скрыт методом с одинаковыми именами в производном типе, если сигнатура параметра производного метода отличается только типами, которые являются более слабыми, чем соответствующие типы в сигнатуре параметра базового метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалить или переименовать метод изменить подпись параметра, чтобы метод не скрывает базовый метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере метод, который нарушает правило.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]