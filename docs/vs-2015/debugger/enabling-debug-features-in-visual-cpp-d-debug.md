---
title: Включение отладки в Visual C++ (-D_DEBUG) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cffa8592c2048c6c6b39eee5c4ca654c41448933
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686705"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Включение параметров отладки в Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] такие возможности отладки, как утверждения, доступны при компиляции программы с заданным символом **_DEBUG**. **_DEBUG** можно задать одним из двух способов:  
  
- Указать **# define _DEBUG** в исходном коде.  
  
- Указать параметр компилятора **/D_DEBUG**. (При создании проекта в Visual Studio с использованием мастеров **/D_DEBUG** задается автоматически в конфигурации отладчика.)  
  
  Когда задан параметр **_DEBUG**, компилятор компилирует разделы кода, заключенные между операторами **#ifdef _DEBUG** и `#endif`.  
  
  Конфигурация отладчика программы MFC должна компоноваться с версией отладчика библиотеки MFC. Файлы заголовков MFC определяют точную версию используемой для компоновки библиотеки MFC на основе заданных символов, таких как **_DEBUG** и **_UNICODE**. Дополнительные сведения см. в разделе [Версии библиотеки MFC](https://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
