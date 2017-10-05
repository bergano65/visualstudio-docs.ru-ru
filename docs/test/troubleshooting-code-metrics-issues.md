---
title: "Устранение проблем, связанных с метриками кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: erickson-doug
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 26dc2869ceb16e2c16a74ee52249777394fb666a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

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
