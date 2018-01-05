---
title: "CA1722: Идентификаторы не должны иметь неверные префиксы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 141adcf6e21c7e0c8d737411988e73fbfbece805
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: идентификаторы не должны иметь неверные префиксы
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Идентификатор имеет неверный префикс.  
  
## <a name="rule-description"></a>Описание правила  
 В соответствии с соглашением об именовании, только некоторые элементы программирования могут иметь имена, которые начинаются с особого префикса.  
  
 Имена типов не имеют особого префикса и не должно начинаться с «C». Это правило сообщает о нарушениях именования имена типов, например «CMyClass» и не касается нарушений имена типов, например «Кэш».  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Удалите префикс от идентификатора.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1715: идентификаторы должны иметь правильные префиксы](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)