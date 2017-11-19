---
title: "CA2118: Обзор использования SuppressUnmanagedCodeSecurityAttribute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92728eae21d4a3035f0396957fa643d14ef06e1c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип или член <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> атрибута.  
  
## <a name="rule-description"></a>Описание правила  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>изменяет поведение системы безопасности по умолчанию для элементов, выполняющих неуправляемый код, с помощью COM взаимодействия или вызова неуправляемого кода. Как правило, система открывает [данных и моделирование](/dotnet/framework/data/index) на разрешение неуправляемого кода. Это требование происходит во время выполнения для каждого вызова члена и проверяет каждого участника в стеке вызовов для разрешения. Когда атрибут присутствует, система создает [требования связывания](/dotnet/framework/misc/link-demands) для разрешения: разрешения непосредственно вызывающего метода проверяются во время JIT-компиляции вызывающего объекта.  
  
 Этот атрибут служит в основном для повышения производительности; однако, прирост производительности сопряжен со значительными рисками безопасности. Если атрибут поместить в открытые члены, вызывающие встроенные методы, вызывающие объекты в стеке вызовов (кроме непосредственного вызывающего объекта) не требуется разрешение на выполнение неуправляемого кода неуправляемый код. В зависимости от действий открытого члена и обработки ввода он может разрешить ненадежных вызывающих объектов для доступа к функциям, как правило, недоступны надежному коду.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Зависит от проверок безопасности, чтобы предотвратить вызывающим объектам прямой доступ к адресному пространству текущего процесса. Поскольку данный атрибут обходит обычную безопасность, код может представлять серьезную угрозу, если он может использоваться для чтения или записи в памяти процесса. Обратите внимание, что риск не ограничивается только методами, которые преднамеренно предоставляют доступ к памяти процесса; также присутствует в любом сценарии, где вредоносный код может получить доступ любыми способами, например, предоставляя неожиданным, имеет неправильный формат или недопустимых входных данных.  
  
 Политики безопасности по умолчанию не предоставляет разрешение неуправляемого кода в сборку, пока оно выполняется на локальном компьютере или является членом одной из следующих групп:  
  
-   Группа кода зоны Мой компьютер  
  
-   Группа кода Microsoft строгого имени  
  
-   Группа кода ECMA строгого имени  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Внимательно просмотрите код, чтобы убедиться, что этот атрибут является абсолютной необходимостью. Если вы не знакомы с безопасности управляемого кода или не понимают безопасности с помощью этого атрибута, удалите его из кода. Если атрибут является обязательным, необходимо убедиться, вызывающие объекты нельзя использовать злонамеренного кода. Если код не имеет разрешения на выполнение неуправляемого кода, этот атрибут не влияет и должны быть удалены.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Чтобы отключить предупреждение из этого правила без последствий, необходимо убедиться, что код не должен предоставлять вызывающим объектам доступ к встроенным операциям или ресурсы, которые могут использоваться в злонамеренных целях.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к нарушению правила.  
  
 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере `DoWork` метод предоставляет открытый путь кода к методу вызова платформы `FormatHardDisk`.  
  
 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере, открытый метод `DoDangerousThing` вызывает нарушение. Чтобы устранить нарушение, `DoDangerousThing` должен быть сделан закрытым и доступ к нему должен предоставляться через открытый метод, защищенный требованием безопасности, как показано в `DoWork` метод.  
  
 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)   
 [Оптимизация безопасности](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [Данные и моделирование](/dotnet/framework/data/index)  
 [Требования связывания](/dotnet/framework/misc/link-demands)  
  