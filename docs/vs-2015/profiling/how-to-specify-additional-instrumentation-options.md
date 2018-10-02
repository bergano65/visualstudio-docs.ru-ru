---
title: Практическое руководство. Указание дополнительных параметров инструментирования | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1726a8ad414ca6450f056044d520f73021c59f46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563467"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Практическое руководство. Указание дополнительных параметров инструментирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: укажите дополнительные параметры инструментирования](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-additional-instrumentation-options).  
  
Инструментирование двоичных файлов можно выполнять в интегрированной среде разработки (IDE) [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] или с помощью средств командной строки. Если инструментирование двоичных файлов выполняется в интегрированной среде разработки, вы можете управлять объемом данных, собираемых во время инструментирование, указав дополнительные параметры инструментирования для программы [VSInstr](../profiling/vsinstr.md). Эти параметры доступны в сеансе или целевом уровне. Например, для включения или исключения конкретных функций во время процесса инструментирования используется дополнительный параметр инструментирования на целевом уровне.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
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



