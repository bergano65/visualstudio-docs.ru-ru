---
title: 'CA2106: обеспечьте Безопасность утверждений | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 67d1228b7684b2ba00a7e64f3755fb107fa0e75b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591876"
---
# <a name="ca2106-secure-asserts"></a>CA2106: обеспечьте безопасность утверждений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2106 Обеспечьте: обеспечьте безопасность утверждений](https://docs.microsoft.com/visualstudio/code-quality/ca2106-secure-asserts).

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
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Правила написания безопасного кода](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)



