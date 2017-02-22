---
title: "Набор правил &quot;Правила глобализации&quot; для управляемого кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Набор правил &quot;Правила глобализации&quot; для управляемого кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Набор правил "Правила глобализации корпорации Майкрософт" позволяет сосредоточиться на проблемах, которые могут препятствовать правильному отображению данных в приложении на различных языках, для разных языковых стандартов и региональных параметров.  Этот набор правил следует добавлять, если для приложения выполняется локализация, глобализация или и то, и другое.  
  
|Правило|Описание|  
|-------------|--------------|  
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Укажите MessageBoxOptions|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Избегайте повторяющихся сочетаний клавиш быстрого доступа|  
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Не следует жестко кодировать строки, зависящие от языка|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Не передавайте литералы в виде локализованных параметров|  
|[CA1304](../Topic/CA1304:%20Specify%20CultureInfo.md)|Укажите CultureInfo|  
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Укажите IFormatProvider|  
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Укажите языковой стандарт для типов данных|  
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Укажите StringComparison|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Нормализуйте строки в верхнем регистре|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Используйте порядковый параметр StringComparison|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Укажите тип маршалинга для строковых аргументов P\/Invoke|