---
title: Набор правил "Правила глобализации" для управляемого кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1630769b5150d9cef7b00e575ac9c555f5bc5be1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667607"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Набор правил "Правила глобализации" для управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Набор правил "Правила глобализации Майкрософт" позволяет сосредоточиться на проблемах, которые могут препятствовать правильному отображению данных в приложении на разных языках, языковых стандартах и культурах. Этот набор правил следует включать, если приложение локализовано, глобализовано или и то, и другое.

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
