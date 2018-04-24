---
title: 'CA1308: строки следует нормализовать в верхнем регистре'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: ffdc7e52b056ac9ab4d06e29d29b8cd5a7b06358
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: строки следует нормализовать в верхнем регистре
|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Операция нормализует строку в нижний регистр.

## <a name="rule-description"></a>Описание правила
 Строки следует нормализовать в верхний регистр. Небольшая группа символов, когда они преобразуются в нижний регистр, не может участвовать в круговом. Чтобы участвовать в круговом возможность преобразовать символы из одного языка на другой язык, который представляет символьные данные по-разному, а затем точно получить исходные символы из преобразованных символов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Изменить операции, которые преобразуют строки в нижний регистр, чтобы строки преобразуются в верхний регистр. Например, измените `String.ToLower(CultureInfo.InvariantCulture)` на `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно отключать предупреждение, если вы не выполняете решение безопасности на основе результата (например, когда он отображается в пользовательском Интерфейсе).

## <a name="see-also"></a>См. также
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)