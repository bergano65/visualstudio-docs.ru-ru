---
title: CA1308. Нормализуйте строки в верхний регистр
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf3acc0911f82a95bde3ce51a8869227c817e49a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894971"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308. Нормализуйте строки в верхний регистр

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Операция нормализует строку в нижний регистр.

## <a name="rule-description"></a>Описание правила
 Строки следует нормализовать в верхний регистр. Небольшая группа символов, когда они преобразуются в нижний регистр, не может участвовать в круговом. Чтобы участвовать в круговом перемещении означает, что для преобразования символов в разных национальных настройках другой языковой стандарт, который представляет символьные данные по-разному, а затем точно получить исходные символы из преобразованных символов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Изменить операции, которые преобразуют строки в нижний регистр, чтобы строки преобразуются в верхний регистр. Например, измените `String.ToLower(CultureInfo.InvariantCulture)` на `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение, если вы не выполняете решение безопасности на основе результата (например, если он отображается в пользовательском Интерфейсе).

## <a name="see-also"></a>См. также
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)