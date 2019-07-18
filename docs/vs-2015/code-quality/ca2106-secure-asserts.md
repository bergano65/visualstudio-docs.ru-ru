---
title: CA2106. Обеспечьте безопасность утверждений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1fb1968c6e2750f658f39f009c97fbab133cccab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687408"
---
# <a name="ca2106-secure-asserts"></a>CA2106. Обеспечьте безопасность утверждений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод подтверждает разрешения без выполнения проверок безопасности для вызывающего объекта.

## <a name="rule-description"></a>Описание правила
 Подтверждение разрешений безопасности без выполнения проверок безопасности может привести к возникновению в коде уязвимости системы безопасности, которой могут воспользоваться злоумышленники. Стека безопасности прекращается после подтверждения разрешения безопасности. Если вы утверждаете разрешение без выполнения проверок на вызывающий объект, вызывающий объект косвенно выполнить код, используя ваши разрешения. Подтверждения без проверок безопасности допустимы, только если есть уверенность, что утверждение не может использоваться в злонамеренных целях. Assert безвредным, если код, который вы вызываете не опасна, или пользователи не будут передаваться произвольные сведения в вызываемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте требование безопасности к методу или его объявляющий тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только после тщательной проверки безопасности.

## <a name="see-also"></a>См. также
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Правила написания безопасного кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
