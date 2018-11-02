---
title: Включение отладки в Visual C++ (-D_DEBUG) | Документация Майкрософт
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
ms.openlocfilehash: e512620e1af8da85039ed403d4280568101fbe57
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829265"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Включение параметров отладки в Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], возможности отладки, такие как утверждения, доступны при компиляции программы с символом **_DEBUG** определен. Вы можете определить **_DEBUG** одним из двух способов:  
  
- Укажите **#define _DEBUG** в исходном коде, или  
  
- Укажите **/D_DEBUG** параметр компилятора. (При создании проекта в Visual Studio с использованием мастеров **/D_DEBUG** автоматически определяется в конфигурации отладки.)  
  
  Когда **_DEBUG** будет определена, компилятор компилирует разделы кода, заключив его в **#ifdef _DEBUG** и `#endif`.  
  
  Конфигурация отладчика программы MFC должна компоноваться с версией отладчика библиотеки MFC. Файлы заголовков MFC определить правильную версию для компоновки библиотеки MFC на основе символов, которые вы определили, такие как **_DEBUG** и **_UNICODE**. Дополнительные сведения см. в разделе [версии библиотек MFC](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)



