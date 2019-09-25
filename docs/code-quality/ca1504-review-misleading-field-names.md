---
title: CA1504. Проверьте имена полей, которые могут ввести в заблуждение
ms.date: 11/04/2016
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
ms.openlocfilehash: 31c147c67854dd59f1fb7c9202f553edfb4a77a8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234509"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504. Проверьте имена полей, которые могут ввести в заблуждение

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Имя поля экземпляра начинается с «s_», а имя `static` поля (`Shared` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) начинается с «m_».

## <a name="rule-description"></a>Описание правила
Имена полей, начинающиеся с "s_", связываются с статическими данными несколькими пользователями. Аналогичным образом имена полей, начинающиеся с "m_", связываются с данными экземпляра (члена). Для упрощения поддержки кода имена должны следовать соглашениям об общем использовании.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, переименуйте поле с помощью соответствующего префикса. Кроме того, можно сделать поле согласен с текущим суффиксом, добавив или `static` удалив модификатор.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.