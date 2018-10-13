---
title: Набор управляемых правил минимальный правила для управляемого кода | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: f67b9e28069a1717ad500b7e8895a363db715fda
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251071"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Набор правил "Минимальные правила для управляемого кода"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Минимальные правила общего доступа к управляемых сосредоточиться на наиболее важными проблемами в коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Следует включать этот набор правил во все пользовательские наборы правил, создаваемые для проектов.  
  
|Правило|Описание|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые завершающие методы|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузка оператора равенства на переопределяющем типе ValueType.Equals|



