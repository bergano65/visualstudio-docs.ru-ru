---
title: CA1308. Нормализуйте строки в верхний регистр
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06fe8d4fbd4def14bfb8a24f4f211a121c809930
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922236"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308. Нормализуйте строки в верхний регистр

|||
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

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Если вы не принимаете решение о безопасности на основе результата (например, при отображении в пользовательском интерфейсе), можно спокойно отключить вывод предупреждающего сообщения.

## <a name="see-also"></a>См. также
[Предупреждения глобализации](../code-quality/globalization-warnings.md)