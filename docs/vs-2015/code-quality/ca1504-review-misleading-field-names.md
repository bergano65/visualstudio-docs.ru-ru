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
ms.openlocfilehash: d375b64bbc877cb377157f13b3e4cfa7c7cf1592
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547879"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504. Проверьте имена полей, которые могут ввести в заблуждение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Имя поля экземпляра начинается с "s_", а имя `static` `Shared` поля (в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) начинается с "m_".

## <a name="rule-description"></a>Описание правила
 Имена полей, начинающиеся с "s_", связываются с статическими данными несколькими пользователями. Аналогичным образом имена полей, начинающиеся с "m_", связываются с данными экземпляра (члена). Для упрощения поддержки кода имена должны следовать соглашениям об общем использовании.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименуйте поле с помощью соответствующего префикса. Кроме того, можно сделать поле согласен с текущим суффиксом, добавив или удалив `static` модификатор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.
