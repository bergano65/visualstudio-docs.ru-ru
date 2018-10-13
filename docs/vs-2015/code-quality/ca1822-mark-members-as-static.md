---
title: 'CA1822: Помечайте члены как статические | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7b85d12038d4c505f912dd2f9440829f2c80679c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183499"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: помечайте члены как статические
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [CA1822: помечайте члены как статические](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Non критическое, если член не видимый за пределами сборки, независимо от того, изменения вносятся. Не критическое, если к члену экземпляра с помощью всего лишь изменить элемент `this` ключевое слово.<br /><br /> Критическое, если элемент изменяется экземпляра в статический член, и отображается за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Элемент, который не осуществляет доступ к данным экземпляра не помечен как статический (Shared в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
## <a name="rule-description"></a>Описание правила  
 Члены, не обращающиеся к данным экземпляра и не вызывающие методы экземпляра, можно пометить как статические (Shared в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Если пометить методы как статические, компилятор предоставит этим членам невиртуальные места вызова. Выпуск невиртуальные места вызова не позволит проверку во время выполнения для каждого вызова, который гарантирует, что текущий указатель на объект не равно null. Это можно достичь измеримое производительности по сравнению с учетом производительности кода. В некоторых случаях отказ в доступе к текущему экземпляру объекта представляет проблему правильность.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Пометьте член как static (или совместно в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) или используйте «this» / «Me» в методе body, при необходимости.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила для ранее созданного кода, для которого будет критическим изменением.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)

