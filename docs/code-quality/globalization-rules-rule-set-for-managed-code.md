---
title: Набор правил "Правила глобализации" для управляемого кода
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0c3b899ec8e19160d9ee4a307a86c576d217004c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658546"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Набор правил "Правила глобализации" для управляемого кода

Используйте набор правил "Правила глобализации Майкрософт", чтобы сосредоточиться на проблемах, которые могут препятствовать правильному отображению данных в приложении на разных языках, языковых стандартах и культурах. Этот набор правил следует включать, если приложение локализовано, глобализовано или и то, и другое.

|Правило|Описание|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Не передавайте литералы в качестве локализованных параметров|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|Указывайте CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|Указывайте IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Укажите StringComparison для ясности|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Нормализуйте строки в верхний регистр|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Используйте порядковый параметр StringComparison|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Укажите StringComparison для корректности|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Укажите тип маршалинга для строковых аргументов P/Invoke|
