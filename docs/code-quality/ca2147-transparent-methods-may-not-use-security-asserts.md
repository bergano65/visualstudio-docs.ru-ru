---
title: "CA2147: прозрачные методы могут не использовать утверждения безопасности | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2147: прозрачные методы могут не использовать утверждения безопасности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Код, помеченный атрибутом <xref:System.Security.SecurityTransparentAttribute>, не обладает достаточными разрешениями для утверждения.  
  
## Описание правила  
 В этом правиле выполняется анализ всех методов и типов в сборки, которая либо на 100% прозрачная, либо смешанная \(прозрачная и критическая\); правило помечает декларативное и императивное использование <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 Во время выполнения любые вызовы <xref:System.Security.CodeAccessPermission.Assert%2A> из прозрачного кода приведут к возникновению <xref:System.InvalidOperationException>.  Это может произойти и в прозрачных на 100% сборках, и в смешанных сборках \(прозрачных и критических\), где метод или тип объявляется прозрачным, но включает декларативный или императивный вызов Assert.  
  
 В версии 2.0 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] представлена новая функция, которая называется *прозрачность*.  Отдельные методы, поля, интерфейсы, классы и типы могут быть либо прозрачными, либо критическими.  
  
 При повышении привилегий безопасности использование прозрачного кода не допускается.  Поэтому все предоставляемые и запрашиваемые разрешения автоматически передаются через код вызывающему объекту или основному домену приложения.  Пример передачи включает элементы Assert, LinkDemand, SuppressUnmanagedCode и код `unsafe`.  
  
## Устранение нарушений  
 Чтобы устранить эту проблему, либо пометьте код, вызывающий Assert с помощью <xref:System.Security.SecurityCriticalAttribute> как SecurityCritical, либо удалите Assert.  
  
## Отключение предупреждений  
 Не следует отключать вывод предупреждений для этого правила.  
  
## Пример  
 Код выдаст сбой, если `SecurityTestClass` является прозрачным при создании методом `Assert` исключения <xref:System.InvalidOperationException>.  
  
 [!CODE [FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts#1)]  
  
## Пример  
 Одним из вариантов является анализ кода метода SecurityTransparentMethod в приведенном ниже примере, и если метод считается безопасным для повышения уровня прав, пометьте SecurityTransparentMethod как критичный в плане безопасности. Это требует выполнения подробного, полного и свободного от ошибок безопасности аудита метода вместе с любыми вызовами, которые возникают в этом методе в Assert:  
  
 [!CODE [FxCop.Security.SecurityTransparentCode2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2#1)]  
  
 Другой возможный вариант — удалить Assert из кода и направить все последующие запросы разрешений на ввод\-вывод файлов за пределы метода SecurityTransparentMethod вызывающего объекта.  Это разрешает выполнение проверок безопасности.  В этом случае аудит безопасности не нужен, поскольку запросы разрешений будут переданы вызывающему объекту или домену приложения.  Управление запросами разрешений осуществляется посредством политики безопасности, среды размещения и разрешений кода.  
  
## См. также  
 [Предупреждения безопасности](../code-quality/security-warnings.md)