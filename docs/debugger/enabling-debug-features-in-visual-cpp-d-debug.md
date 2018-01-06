---
title: "Включение параметров отладки в Visual C++ (-D_DEBUG) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f1067ee5b60b8a8a402c9612357f2d83b6da138
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Включение параметров отладки в Visual C++ (/D_DEBUG)
В [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], возможности отладки, такие как утверждения, доступны при компиляции программы с заданным символом **_DEBUG** определен. Можно определить **_DEBUG** одним из двух способов:  
  
-   Укажите **#define _DEBUG** в исходном коде, или  
  
-   Укажите **/D_DEBUG** параметр компилятора. (При создании проекта в Visual Studio с использованием мастеров, **/D_DEBUG** определяется автоматически в конфигурации отладчика.)  
  
 Когда **_DEBUG** будет определена, компилятор компилирует разделы кода, окруженный **#ifdef _DEBUG** и `#endif`.  
  
 Конфигурация отладчика программы MFC должна компоноваться с версией отладчика библиотеки MFC. Файлы заголовков MFC определяют правильную версию для компоновки библиотеки MFC на основе символов, которые вы определили, таких как **_DEBUG** и **_UNICODE**. Дополнительные сведения см. в разделе [версии библиотек MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)