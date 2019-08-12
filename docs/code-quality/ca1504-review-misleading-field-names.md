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
ms.openlocfilehash: df6ab704c2dfdbf8ebdf8eb42f56d8d64600736f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921829"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504. Проверьте имена полей, которые могут ввести в заблуждение

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Имя поля экземпляра начинается с «s_», а имя `static` поля (`Shared` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) начинается с «m_».

## <a name="rule-description"></a>Описание правила
Имена полей, начинающиеся с "s_", связываются с статическими данными несколькими пользователями. Аналогичным образом имена полей, начинающиеся с "m_", связываются с данными экземпляра (члена). Для упрощения поддержки кода имена должны следовать соглашениям об общем использовании.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, переименуйте поле с помощью соответствующего префикса. Кроме того, можно сделать поле согласен с текущим суффиксом, добавив или `static` удалив модификатор.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.