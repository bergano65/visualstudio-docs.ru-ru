---
title: 'CA2101: Укажите тип маршалинга для строковых аргументов P / Invoke | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2ff14e50af33b5b779244109916c91abff2663c3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238690"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: укажите тип маршалинга для строковых аргументов P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Неуправляемого член позволяет частично доверенным вызывающим объектам, содержит строковый параметр и явным образом не маршалинга этой строки.

## <a name="rule-description"></a>Описание правила
 При преобразовании из Юникода в ANSI, вполне возможно, что не все символы Юникода могут быть представлены в конкретной кодовой страницы ANSI. *Наилучшее сопоставление* пытается решить эту проблему, подстановка символа для символа, который не может быть представлено. Использование этой функции может привести к уязвимости системы безопасности, поскольку вы не можете управлять символ, который выбран. Например, вредоносный код может преднамеренно создать строку Юникода, которая содержит символы, которые не находятся в конкретной кодовой страницы, которые преобразуются в специальные знаки файловой системы, такие как ".." или «/». Обратите внимание, что проверки безопасности для специальных символов часто происходят прежде, чем строка преобразуется в формат ANSI.

 Наилучшее сопоставление по умолчанию для неуправляемых преобразования WChar в МБ. Если вы явно отключить наилучшего соответствия, ваш код может содержать уязвимые места, из-за этой проблемы.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явного маршалинга строковых типов данных.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере метод, который нарушает это правило и демонстрируется, как устранить нарушение.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]



