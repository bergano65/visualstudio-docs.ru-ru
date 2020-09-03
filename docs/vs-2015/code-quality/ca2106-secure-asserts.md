---
title: 'CA2106: безопасные утверждения | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547749"
---
# <a name="ca2106-secure-asserts"></a>CA2106. Обеспечьте безопасность утверждений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод подтверждает разрешения без выполнения проверок безопасности для вызывающего объекта.

## <a name="rule-description"></a>Описание правила
 Подтверждение разрешений безопасности без выполнения проверок безопасности может привести к возникновению в коде уязвимости системы безопасности, которой могут воспользоваться злоумышленники. Проверка стека безопасности останавливается при утверждении разрешения безопасности. Если вы утверждаете разрешение без выполнения каких-либо проверок вызывающего объекта, вызывающий объект может косвенно выполнить код с помощью разрешений. Утверждения без проверок безопасности доверяются только в том случае, если гарантируется, что утверждение не может быть использовано каким-либо вредоносным способом. Утверждение является безобидным, если код, который вы вызываете, является безобидным, или пользователи не могут передать произвольную информацию в вызываемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте требование безопасности в метод или его объявляющий тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила только после тщательного анализа безопасности.

## <a name="see-also"></a>См. также:
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Правила написания безопасного кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
