---
title: "Набор правил \"Правила глобализации\" для управляемого кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 07a2e8da87eb486f8247a79263ec371a8fd4afc5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Набор правил "Правила глобализации" для управляемого кода
Можно использовать правила глобализации корпорации Майкрософт набора правил в основное внимание уделяется проблемам, которые могут помешать данных в приложении будут правильно отображаться на различных языках, язык и региональные стандарты и языки и региональные параметры. Следует включать этот набор, если приложение локализовано глобализованные, правил или оба.  
  
|Правило|Описание:|  
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