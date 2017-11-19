---
title: "CA2106: обеспечьте Безопасность утверждений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 321d00f13ebc891070549778239fec60201d03c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)