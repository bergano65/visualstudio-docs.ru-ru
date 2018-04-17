---
title: 'CA1716: Идентификаторы не должны совпадать с ключевыми словами | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c695f66a096614621cee2f38aed3e8fd6d970bed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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