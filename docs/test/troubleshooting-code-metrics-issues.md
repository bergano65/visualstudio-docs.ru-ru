---
title: "Устранение проблем, связанных с метриками кода | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: "4"
author: erickson-doug
ms.author: douge
manager: douge
ms.openlocfilehash: 6dde34ce4808f21a90fa9d2e37daf7ed88d4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-code-metrics-issues"></a>Устранение неполадок, связанных с метриками кода
Во время сбора метрик кода могут возникать некоторые из следующих проблем:  
  
-   [Изменения в вычислениях сложности кода Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Изменения в вычислениях сложности кода Visual Studio 2010  
 Для одной и той же функции метрика сложности кода, вычисленная в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], может отличаться от метрики, вычисленной в более ранних версиях [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], в указанных ниже ситуациях.  
  
-   Функция содержит один или несколько блоков catch. В предыдущих версиях [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] блоки catch не включались в вычисления. В [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] сложность каждого блока catch прибавляется к сложности функции.  
  
-   Функция содержит оператор switch (Select Case в VB). Различия в компиляторах между [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] и более ранними версиями могут приводить к созданию разного кода MSIL для некоторых операторов switch, в которых имеются случаи передачи управления.  
  
## <a name="see-also"></a>См. также  
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)