---
title: 'CA1504: Проверка имен полей с ошибочным заполнением | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3f1cca5dd33047a4d19c78013dd535e0e9dd6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607753"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: проверьте имена полей, которые могут ввести в заблуждение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Имя поля экземпляра начинается с "s_" или имени поля `static` (`Shared` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) начинается с "m_".

## <a name="rule-description"></a>Описание правила
 Имена полей, начинающиеся с "s_", связываются с статическими данными несколькими пользователями. Аналогичным образом имена полей, начинающиеся с "m_", связываются с данными экземпляра (члена). Для упрощения поддержки кода имена должны следовать соглашениям об общем использовании.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименуйте поле с помощью соответствующего префикса. Кроме того, можно сделать поле согласен с текущим суффиксом, добавив или удалив модификатор `static`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.
