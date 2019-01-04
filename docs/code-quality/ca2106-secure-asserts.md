---
title: CA2106. Обеспечьте безопасность утверждений
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164d2bbe335f4b69892cf069bade5cf0df1e0787
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864677"
---
# <a name="ca2106-secure-asserts"></a>CA2106. Обеспечьте безопасность утверждений

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод подтверждает разрешения и выполняет проверки безопасности, не в вызывающем объекте.

## <a name="rule-description"></a>Описание правила
 Подтверждение разрешений безопасности без выполнения проверок безопасности может привести к возникновению в коде уязвимости системы безопасности, которой могут воспользоваться злоумышленники. Стека безопасности прекращается после подтверждения разрешения безопасности. Если вы утверждаете разрешение без выполнения проверок на вызывающий объект, вызывающий объект косвенно выполнить код, используя ваши разрешения. Подтверждения без проверок безопасности допустимы, если вы уверены, что утверждение не может использоваться в злонамеренных целях. Assert можно удалить, если код, который вы вызываете не опасна, или в том случае, если пользователи не будут передаваться произвольные сведения в вызываемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте требование безопасности к методу или его объявляющий тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только после тщательной проверки безопасности.

## <a name="see-also"></a>См. также

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)