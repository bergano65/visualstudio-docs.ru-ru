---
title: "CA1823: Избегайте наличия неиспользованных закрытых полей | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f4be67d74c3b0b01092d43d70c3c37a776def14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: избегайте наличия неиспользованных закрытых полей
|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Это правило появляется в том случае, когда существует закрытое поле в коде, но не используется, все пути кода.  
  
## <a name="rule-description"></a>Описание правила  
 Обнаружены закрытые поля, доступ к которым, судя по всему, не предоставляется в сборке.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите поле или добавьте код, который его использует.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)