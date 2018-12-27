---
title: Устранение неполадок, связанных с метриками кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9575020135846edc9cb86bd89ff72682500d8a9d
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739566"
---
# <a name="troubleshooting-code-metrics-issues"></a>Устранение неполадок, связанных с метриками кода
Во время сбора метрик кода могут возникать некоторые из следующих проблем:

-   [Изменения в вычислениях сложности кода Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Изменения в вычислениях сложности кода Visual Studio 2010
 Для одной и той же функции метрика сложности кода, вычисленная в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], может отличаться от метрики, вычисленной в более ранних версиях [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], в указанных ниже ситуациях.

- Функция содержит один или несколько блоков catch. В предыдущих версиях [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] блоки catch не включались в вычисления. В [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] сложность каждого блока catch прибавляется к сложности функции.

- Функция содержит оператор switch (Select Case в VB). Различия в компиляторах между [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] и более ранними версиями могут приводить к созданию разного кода MSIL для некоторых операторов switch, в которых имеются случаи передачи управления.

## <a name="see-also"></a>См. также
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md)