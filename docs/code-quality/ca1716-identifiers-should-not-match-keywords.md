---
title: "CA1716: Идентификаторы не должны совпадать с ключевыми словами | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 619fc7867d14a26f2c3b674b4b8ac8b2d8fba114
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: идентификаторы не должны совпадать с ключевыми словами
|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя пространства имен, типа или члена виртуального члена или интерфейс совпадает с зарезервированным ключевым словом языка программирования.  
  
## <a name="rule-description"></a>Описание правила  
 Идентификаторы пространств имен, типов и виртуальные члены интерфейса не должен совпадать с ключевыми словами, определенными в языках, предназначенных для общеязыковой. В зависимости от используемого языка и ключевого слова ошибки или неоднозначности компилятора могут затруднять библиотеку для использования.  
  
 Это правило проверяет с ключевыми словами на следующих языках:  
  
-   Visual Basic  
  
-   C#  
  
-   C++/CLI  
  
 Сравнение без учета регистра используется для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ключевые слова и сравнение с учетом регистра используется для других языков.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Выберите имя, которое не отображается в списке ключевых слов.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно подавить предупреждение из этого правила, если вы уверены, что идентификатор не путайте пользователей API-интерфейса и может использоваться в некоторых языках, библиотеку [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].