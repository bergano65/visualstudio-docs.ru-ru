---
title: "Устранение проблем, связанных с метриками кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ef318d7c71a5770ea7a78ff078340b4f2dff960
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-metrics-issues"></a>Устранение неполадок, связанных с метриками кода
Во время сбора метрик кода могут возникать некоторые из следующих проблем:  
  
-   [Изменения в вычислениях сложности кода Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Изменения в вычислениях сложности кода Visual Studio 2010  
 Для той же функции, вычисленные метрика сложности кода, в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] может отличаться от метрики, вычисленной в более ранних версиях [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] в следующих ситуациях:  
  
-   Функция содержит один или несколько блоков catch. В предыдущих версиях [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], catch, блоки не были включены в расчет. В [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], добавить к сложности функции сложность каждого блока catch.  
  
-   Функция содержит оператор switch (Select Case в VB). Различия в компиляторе [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] и более ранних версиях можно создать другой код MSIL для некоторых switch, которые содержат проходом при невыполнении условия.  
  
## <a name="see-also"></a>См. также  
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)