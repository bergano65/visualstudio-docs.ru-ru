---
title: Включение отладки в Visual C++ (-D_DEBUG) | Документация Майкрософт
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
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67de755105f30ee4a88daeef26bc29bc9841ae39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562202"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Включение параметров отладки в Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Включение функции отладки в Visual C++ (-D_DEBUG)](https://docs.microsoft.com/visualstudio/debugger/enabling-debug-features-in-visual-cpp-d-debug).  
  
В [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], возможности отладки, такие как утверждения, доступны при компиляции программы с символом **_DEBUG** определен. Вы можете определить **_DEBUG** одним из двух способов:  
  
-   Укажите **#define _DEBUG** в исходном коде, или  
  
-   Укажите **/D_DEBUG** параметр компилятора. (При создании проекта в Visual Studio с использованием мастеров **/D_DEBUG** автоматически определяется в конфигурации отладки.)  
  
 Когда **_DEBUG** будет определена, компилятор компилирует разделы кода, заключив его в **#ifdef _DEBUG** и `#endif`.  
  
 Конфигурация отладчика программы MFC должна компоноваться с версией отладчика библиотеки MFC. Файлы заголовков MFC определить правильную версию для компоновки библиотеки MFC на основе символов, которые вы определили, такие как **_DEBUG** и **_UNICODE**. Дополнительные сведения см. в разделе [версии библиотек MFC](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)



