---
title: Практическое руководство. Указание дополнительных параметров инструментирования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2440f31b6a6ac345644e20e14b4a82972967fab
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104282"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Практическое руководство. Указание дополнительных параметров инструментирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Инструментирование двоичных файлов можно выполнять в интегрированной среде разработки (IDE) [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] или с помощью средств командной строки. Если инструментирование двоичных файлов выполняется в интегрированной среде разработки, вы можете управлять объемом данных, собираемых во время инструментирование, указав дополнительные параметры инструментирования для программы [VSInstr](../profiling/vsinstr.md). Эти параметры доступны в сеансе или целевом уровне. Например, для включения или исключения конкретных функций во время процесса инструментирования используется дополнительный параметр инструментирования на целевом уровне.  
  
 **Требования**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
>  Каждый вставленный зонд незначительно изменяет поведение исходной программы. Это изменение приводит к увеличению времени анализа. Несмотря на то, что приблизительное значение этих временных затрат вычитается, они оказывают небольшое влияние на многопоточные приложения. Параметры программы [VSInstr](../profiling/vsinstr.md) позволяют управлять сбором данных во время профилирования.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Указание дополнительных параметров инструментирования  
  
1. В **обозревателе производительности** выберите **Сеанс производительности**, а затем щелкните его правой кнопкой мыши и выберите **Свойства**.  
  
2. В окне **Страницы свойств** щелкните **дополнительные** свойства.  
  
3. Введите параметры в поле **Дополнительные параметры инструментирования**.  
  
     Например, используйте параметр /CONTROL:THREAD для указания уровня профилирования. Полный список параметров см. в разделе [VSInstr](../profiling/vsinstr.md).  
  
4. Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)
