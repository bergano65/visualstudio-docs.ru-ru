---
title: Практическое руководство. Перемещение инструментированных двоичных файлов | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d0ddfb3cd52e212965ebf928bf087519f38b0bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240985"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Практическое руководство. Перемещение инструментированных двоичных файлов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Во время инструментирования в двоичный файл вставляются зонды для измерения производительности приложения. При перемещении инструментированного двоичного файла копия оригинального двоичного файла инструментируется и помещается в указанное расположение. Этот вариант полезен, если вы не хотите, чтобы профилировщик переименовал ваш исходный двоичный файл. Если двоичный файл не перемещается, будет перезаписана оригинальная версия двоичного файла.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Перемещение инструментированного двоичного файла  
  
1.  В **обозревателе производительности**щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.  
  
2.  На **страницах свойств**щелкните пункт **Двоичный файл** .  
  
3.  Установите флажок **Переместить инструментированные двоичные файлы** .  
  
4.  Укажите расположение для инструментированного двоичного файла.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



