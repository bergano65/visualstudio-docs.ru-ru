---
title: Набор управляемых правил минимальный правила для управляемого кода | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cca9670f65ef517a4697fc0752c65cbafbaa3b16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561237"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Набор правил "Минимальные правила для управляемого кода"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [набор правил управляемых минимальный правила для управляемого кода](https://docs.microsoft.com/visualstudio/code-quality/managed-minimun-rules-rule-set-for-managed-code).  
  
Минимальные правила общего доступа к управляемых сосредоточиться на наиболее важными проблемами в коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Следует включать этот набор правил во все пользовательские наборы правил, создаваемые для проектов.  
  
|Правило|Описание|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые завершающие методы|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузка оператора равенства на переопределяющем типе ValueType.Equals|



