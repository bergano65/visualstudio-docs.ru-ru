---
title: Набор правил "Правила глобализации" для управляемого кода
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28199eb9fa09e2096939ffa8e678eb9812a61b1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816404"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Набор правил "Правила глобализации" для управляемого кода
Можно использовать правила глобализации корпорации Майкрософт набора правил в основное внимание уделяется проблемам, которые могут препятствовать данных в приложении неправильно отображалось в разных языках, регионов и языков и региональных параметров. Следует включать этот набор, если приложение выполняется локализация, глобализация, правил или оба.

|Правило|Описание|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Укажите MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Избегайте повторяющихся акселераторов|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Не указывайте прямо в коде строки, зависящие от языковых стандартов|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Не передавайте литералы в качестве локализованных параметров|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Указывайте CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Указывайте IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Задавайте языковой стандарт для типов данных|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Указывайте StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Нормализуйте строки в верхний регистр|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Используйте порядковый параметр StringComparison|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Укажите тип маршалинга для строковых аргументов P/Invoke|