---
title: DA0011. Затратный метод CompareTo | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06e723fc30bfde69344218beaca4e1c0b3c5d742
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804167"
---
# <a name="da0011-expensive-compareto"></a>DA0011. Затратный метод CompareTo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [DA0011: Затратное CompareTo](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|Идентификатор правила|DA0011|  
|Категория|Использование .NET Framework|  
|Методы профилирования|Дискретизация<br /><br /> Память .NET|  
|Сообщение|Функции CompareTo должны быть малозатратными и не выделять память. Если возможно, уменьшите сложность функции CompareTo.|  
|Тип правила|Предупреждение|  
  
## <a name="cause"></a>Причина  
 Метод CompareTo типа является затратным или выделяет память.  
  
## <a name="rule-description"></a>Описание правила  
 Методы CompareTo должны быть эффективными и не выделять память.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Упростите метод CompareTo.
