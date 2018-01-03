---
title: "Практическое руководство. Перемещение инструментированных двоичных файлов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72c15bfc5449a1dab516be217da4a76276312fd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-relocate-instrumented-binaries"></a>Практическое руководство. Перемещение инструментированных двоичных файлов
Во время инструментирования в двоичный файл вставляются зонды для измерения производительности приложения. При перемещении инструментированного двоичного файла копия оригинального двоичного файла инструментируется и помещается в указанное расположение. Этот вариант полезен, если вы не хотите, чтобы профилировщик переименовал ваш исходный двоичный файл. Если двоичный файл не перемещается, будет перезаписана оригинальная версия двоичного файла.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Перемещение инструментированного двоичного файла  
  
1.  В **обозревателе производительности**щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.  
  
2.  На **страницах свойств**щелкните пункт **Двоичный файл** .  
  
3.  Установите флажок **Переместить инструментированные двоичные файлы** .  
  
4.  Укажите расположение для инструментированного двоичного файла.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)