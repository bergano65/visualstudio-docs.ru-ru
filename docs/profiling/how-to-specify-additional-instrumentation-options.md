---
title: "Практическое руководство. Указание дополнительных параметров инструментирования | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c663b4de5f35df1d0fb1bdcfda076502360361d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Практическое руководство. Указание дополнительных параметров инструментирования
Инструментирование двоичных файлов можно выполнять в интегрированной среде разработки (IDE) [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] или с помощью средств командной строки. Если инструментирование двоичных файлов выполняется в интегрированной среде разработки, вы можете управлять объемом данных, собираемых во время инструментирование, указав дополнительные параметры инструментирования для программы [VSInstr](../profiling/vsinstr.md). Эти параметры доступны в сеансе или целевом уровне. Например, для включения или исключения конкретных функций во время процесса инструментирования используется дополнительный параметр инструментирования на целевом уровне.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!IMPORTANT]
>  Каждый вставленный зонд незначительно изменяет поведение исходной программы. Это изменение приводит к увеличению времени анализа. Несмотря на то, что приблизительное значение этих временных затрат вычитается, они оказывают небольшое влияние на многопоточные приложения. Параметры программы [VSInstr](../profiling/vsinstr.md) позволяют управлять сбором данных во время профилирования.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Указание дополнительных параметров инструментирования  
  
1.  В **обозревателе производительности** выберите **Сеанс производительности**, а затем щелкните его правой кнопкой мыши и выберите **Свойства**.  
  
2.  В окне **Страницы свойств** щелкните **дополнительные** свойства.  
  
3.  Введите параметры в поле **Дополнительные параметры инструментирования**.  
  
     Например, используйте параметр /CONTROL:THREAD для указания уровня профилирования. Полный список параметров см. в разделе [VSInstr](../profiling/vsinstr.md).  
  
4.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)