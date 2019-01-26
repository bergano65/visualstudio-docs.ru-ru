---
title: CA1504. Проверьте имена полей, которые могут ввести в заблуждение
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da99bab4235028f75146be1807162e93759d3eb9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926466"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504. Проверьте имена полей, которые могут ввести в заблуждение

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Имя поля экземпляра начинается с «s_» или имя `static` (`Shared` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) поля начинается с «m_».

## <a name="rule-description"></a>Описание правила
 Имена полей, начинающиеся с «s_» связаны с статических данных несколькими пользователями. Аналогичным образом имена полей, начинающиеся с «m_» связаны с данными экземпляра (элемент). Для упрощения поддержки кода имена должны следовать тонкостях соглашения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименование поля, используя соответствующий префикс. Кроме того, сделать поле соответствующим суффиксом текущего, добавляя или удаляя `static` модификатор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.