---
title: Включение отладки в Visual C++ (-D_DEBUG) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2c18dfec1f6d1581f926fa24d006b3761c2f6fce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976252"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Включение параметров отладки в Visual C++ (/D_DEBUG)
В [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] такие возможности отладки, как утверждения, доступны при компиляции программы с заданным символом **_DEBUG**. **_DEBUG** можно задать одним из двух способов:  
  
- Указать **# define _DEBUG** в исходном коде.  
  
- Указать параметр компилятора **/D_DEBUG**. (При создании проекта в Visual Studio с использованием мастеров **/D_DEBUG** задается автоматически в конфигурации отладчика.)  
  
  Когда задан параметр **_DEBUG**, компилятор компилирует разделы кода, заключенные между операторами **#ifdef _DEBUG** и `#endif`.  
  
  Конфигурация отладчика программы MFC должна компоноваться с версией отладчика библиотеки MFC. Файлы заголовков MFC определяют точную версию используемой для компоновки библиотеки MFC на основе заданных символов, таких как **_DEBUG** и **_UNICODE**. Дополнительные сведения см. в разделе [Версии библиотеки MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)