---
title: "Набор правил &quot;Минимальные правила для управляемого кода&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 2
---
# Набор правил &quot;Минимальные правила для управляемого кода&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Управляемые минимальные правила сосредоточены на важнейших проблемах существующего кода, в том числе на потенциальных уязвимостях безопасности, причинах сбоев приложений и других важных логических ошибках и ошибках проектирования.  Следует включать этот набор правил во все пользовательские наборы правил, создаваемые для проектов.  
  
|Правило|Описание|  
|-------------|--------------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые методы завершения|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Высвободите высвобождаемые поля|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегружать равенство операторов следует при перегрузке ValueType.Equals|