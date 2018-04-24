---
title: 'CA1504: проверьте имена полей, которые могут ввести в заблуждение'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0caf5e8c158f2c434bd20e4b033ed1e2f7f37e5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: проверьте имена полей, которые могут ввести в заблуждение
|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Имя поля экземпляра начинается с «s_» или имя `static` (`Shared` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) поля начинается с «m_».

## <a name="rule-description"></a>Описание правила
 Имена полей, начинающиеся с «s_» связаны с статических данных несколькими пользователями. Аналогичным образом имена полей, которые начинаются с «m_» связаны с данными экземпляра (элемент). Для упрощения поддержки кода имена должны следовать часто используемые соглашения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, переименование поля, используя соответствующий префикс. Можно также сделать поле соответствующим текущему префиксу, добавив или удалив `static` модификатор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.