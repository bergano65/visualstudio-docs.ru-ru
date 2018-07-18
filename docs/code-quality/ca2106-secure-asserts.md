---
title: 'CA2106: обеспечьте безопасность утверждений'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 5863f4d8ca4db47f7e537f0b1abc5eb280434c80
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916803"
---
# <a name="ca2106-secure-asserts"></a>CA2106: обеспечьте безопасность утверждений
|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод подтверждает разрешения без выполнения проверок безопасности для вызывающего объекта.

## <a name="rule-description"></a>Описание правила
 Подтверждение разрешений безопасности без выполнения проверок безопасности может привести к возникновению в коде уязвимости системы безопасности, которой могут воспользоваться злоумышленники. Обход стека безопасности прекращается после подтверждения разрешения безопасности. Если вы утверждаете разрешение без выполнения проверок для вызывающего объекта, вызывающий объект может неявно выполнить код с помощью разрешений. Подтверждения без проверок безопасности допустимы, только если есть уверенность, что утверждение не может использоваться в злонамеренных целях. Assert можно удалить, если код, вызываемый опасное или пользователи не могут передавать произвольные сведения в вызываемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, добавьте требование безопасности к методу или его объявляющий тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только после тщательной проверки безопасности.

## <a name="see-also"></a>См. также
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)