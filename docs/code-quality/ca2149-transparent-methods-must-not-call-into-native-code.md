---
title: "CA2149: Прозрачные методы должны не вызывать в машинном коде | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 937b6c203b7ee5a2dbe2c77ba1c67ca7500c1fa4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: прозрачные методы не следует вызывать в машинном коде
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Метод вызывает собственную функцию через прототип метода, например P/Invoke.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило срабатывает для любого прозрачного метода, который вызывается непосредственно в машинном коде, например, с помощью вызова P/Invoke. Нарушение этого правила приводит к <xref:System.MethodAccessException> в уровне 2 модели прозрачности и вызову полного требования <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> уровне 1 модели прозрачности.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, пометьте метод, который вызывает машинный код с <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]