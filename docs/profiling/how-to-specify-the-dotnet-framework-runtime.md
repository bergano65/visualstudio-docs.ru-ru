---
title: "Практическое руководство. Определение среды выполнения .NET Framework | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 45baa5754e5ffb44edf948dc39fa80d2249e03f1
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-specify-the-net-framework-runtime"></a>Практическое руководство. Определение среды выполнения .NET Framework
В выпуске [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] можно составлять приложения из модулей, построенных с помощью разных версий среды выполнения [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. По умолчанию средства профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] профилируют первую среду выполнения, загруженную приложением. Можно указать среду выполнения для профилирования при запуске приложения с помощью профилировщика и при подключении профилировщика к уже запущенному приложению.  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Указание профилируемой среды выполнения .NET Framework при запуске приложения с помощью профилировщика  
  
1.  В **обозревателе производительности** щелкните правой кнопкой мыши сеанс анализа производительности, выберите пункт **Свойства**, а затем **Дополнительно**.  
  
     В списке **Целевая версия CLR** отображается **Автоматически** и версия среды выполнения [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], которая установлена на компьютере.  
  
2.  Выполните одно из следующих действий.  
  
    -   Выберите версию среды CLR для профилирования.  
  
    -   Щелкните пункт **Автоматически**, чтобы выполнить профилирование первой версии, загруженной приложением.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Указание профилируемой среды выполнения .NET Framework при подключении профилировщика к приложению  
  
1.  В меню "Анализ" наведите указатель мыши на пункт "Профилировщик" и щелкните "Присоединить/отсоединить".  
  
2.  В диалоговом окне "Присоединить профилировщик к процессу" щелкните процесс, который необходимо профилировать.  
  
     В списке **Целевая версия CLR** отображается **Автоматически** и версии среды выполнения [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], установленные на компьютере.  
  
3.  Выполните одно из следующих действий.  
  
    -   Выберите версию среды CLR для профилирования.  
  
    -   Щелкните **Автоматически** для профилирования версии, загружаемой при подключении профилировщика к приложению.
