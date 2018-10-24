---
title: 'DA0011: затратное CompareTo | Документы Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f6137c07ac6b920234a9772764b5ad758efdb1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818852"
---
# <a name="da0011-expensive-compareto"></a>DA0011: затратное CompareTo

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