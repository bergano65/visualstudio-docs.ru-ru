---
title: "CA2101: Укажите тип маршалинга для строковых аргументов P-Invoke | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a759662b35024add1666e99c89433f0b369676b7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: укажите тип маршалинга для строковых аргументов P/Invoke
|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Неуправляемого член позволяет частично доверенным вызывающим объектам, содержит строковый параметр и не явного маршалинга этой строки.  
  
## <a name="rule-description"></a>Описание правила  
 При преобразовании из Юникода в ANSI, существует возможность, что не все символы Юникода могут использоваться в конкретной кодовой страницы ANSI. *Наилучшее сопоставление* пытается решить эту проблему, подстановка знака для символа, который не может быть представлен. Использование этой функции может привести к уязвимости системы безопасности, поскольку не удается управлять символ, который выбран. Например, вредоносный код может преднамеренно создать строку Юникода, содержащий символы, которые не представлены в конкретной кодовой страницы, которые преобразуются в служебные знаки файловой системы, такие как ".." или «/». Обратите внимание, что проверок безопасности для специальных символов часто происходят прежде, чем строка преобразуется в формат ANSI.  
  
 Наилучшее сопоставление используется по умолчанию для неуправляемых преобразования типа WChar в МБ. Если вы явно отключить наилучшего соответствия, ваш код может содержать уязвимые места, из-за этой проблемы.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, явного маршалинга строковых данных.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метод, который нарушает это правило, а затем показано, как исправить нарушение.  
  
 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]