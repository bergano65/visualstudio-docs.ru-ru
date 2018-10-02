---
title: 'CA1707: Идентификаторы не должны содержать символы подчеркивания | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c34b03e57d1b303ba6a5f782fd5a5de5afe81ad0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572213"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: идентификаторы не должны содержать знак подчеркивания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [CA1707: идентификаторы не должны содержать символы подчеркивания](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — при возникновении на сборки<br /><br /> Не критическое — при возникновении на параметры типа|  
  
## <a name="cause"></a>Причина  
 Имя идентификатора содержит символ подчеркивания (_).  
  
## <a name="rule-description"></a>Описание правила  
 В соответствии с соглашением имена идентификаторов не могут содержать знак подчеркивания (_). Это правило проверяет пространства имен, типов, членов и параметров.  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Удалите все знаки подчеркивания из имени.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

