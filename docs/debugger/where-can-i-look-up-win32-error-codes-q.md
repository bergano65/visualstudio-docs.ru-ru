---
title: Где можно найти коды ошибок Win32? | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81d919733f1caf654460cf342da05f2549dfa167
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Где можно найти коды ошибок Win32?
WINERROR.H в папке INCLUDE стандартного дистрибутива содержит определения кодов ошибок для функций Win32 API.  
  
 Можно посмотреть код ошибки, введя код в **Контрольные значения** окна или **Быстрая проверка** диалоговое окно. Пример:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)