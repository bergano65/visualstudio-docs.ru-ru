---
title: Набор правил "Правила глобализации" для управляемого кода
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3c717eeeb94deee611c4e9cf5da573e1039e13fc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Набор правил "Правила глобализации" для управляемого кода
Можно использовать правила глобализации корпорации Майкрософт набора правил в основное внимание уделяется проблемам, которые могут помешать данных в приложении будут правильно отображаться на различных языках, язык и региональные стандарты и языки и региональные параметры. Следует включать этот набор, если приложение локализовано глобализованные, правил или оба.

|Правило|Описание|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Укажите MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Избегайте повторяющиеся сочетания клавиш|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Не следует жестко кодировать строки|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Не передавать литералы в виде локализованных параметров|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Укажите CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Укажите IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Задавайте языковой стандарт для типов данных|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Укажите StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Строки следует нормализовать в верхний регистр|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Используйте порядковый параметр StringComparison|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Укажите тип маршалинга для строковых аргументов P/Invoke|