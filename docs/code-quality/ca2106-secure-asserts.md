---
title: 'CA2106: обеспечьте Безопасность утверждений | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: c2b49ab6d6cd99dc2865be21a2ed68579922bbb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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