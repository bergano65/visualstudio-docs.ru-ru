---
title: 'CA1308: нормализация строк до верхнего регистра | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c068fcda7d03ae91435c040d2110d632668d832a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538740"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308. Нормализуйте строки в верхний регистр
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Операция нормализует строку в нижний регистр.

## <a name="rule-description"></a>Описание правила
 Строки следует нормализовать в верхний регистр. Небольшая группа символов, при преобразовании в нижний регистр, не может выполнить цикл обработки. Для преобразования символов из одного языкового стандарта в другой языковой стандарт, представляющий символьные данные по-разному, а затем для точного извлечения исходных символов из преобразованных символов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Операции изменения преобразуют строки в нижний регистр, чтобы строки были преобразованы в верхний регистр. Например, измените `String.ToLower(CultureInfo.InvariantCulture)` на `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Если вы не принимаете решение о безопасности на основе результата (например, при отображении в пользовательском интерфейсе), можно спокойно отключить вывод предупреждающего сообщения.

## <a name="see-also"></a>См. также
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)
