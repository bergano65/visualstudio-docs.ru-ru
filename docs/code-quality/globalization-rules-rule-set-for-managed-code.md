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
ms.openlocfilehash: 905f3323f4ede33ba8a7e1547bed7a81c43be96d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449031"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Набор правил "Правила глобализации" для управляемого кода

Используйте набор правил "Правила глобализации Майкрософт", чтобы сосредоточиться на проблемах, которые могут препятствовать правильному отображению данных в приложении на разных языках, языковых стандартах и культурах. Этот набор правил следует включать, если приложение локализовано, глобализовано или и то, и другое.

|Правило|Описание|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Укажите MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Избегайте повторяющихся акселераторов|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Не кодировать строки, зависящие от языкового стандарта|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Не передавайте литералы в качестве локализованных параметров|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Указывайте CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Указывайте IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Задавайте языковой стандарт для типов данных|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Указывайте StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Нормализуйте строки в верхний регистр|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Используйте порядковый параметр StringComparison|
|[CA2101](../code-quality/ca2101.md)|Укажите тип маршалинга для строковых аргументов P/Invoke|
