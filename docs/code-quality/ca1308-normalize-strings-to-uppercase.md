---
title: 'CA1308: Строки следует нормализовать в верхний регистр | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: 979b6d0bbd14d6432ea376622ce61f6329f708fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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