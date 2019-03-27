---
title: 'DA0011: затратное CompareTo | Документы Майкрософт'
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
ms.openlocfilehash: 281bdbb3ba974b3aacb9c349575727675bb59305
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58354769"
---
# <a name="da0011-expensive-compareto"></a>DA0011: затратное CompareTo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio, см. в разделе [DA0011: затратное CompareTo](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) на сайте docs.microsoft.com.  
  
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
