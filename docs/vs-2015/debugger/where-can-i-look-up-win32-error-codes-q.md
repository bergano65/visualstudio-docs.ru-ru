---
title: Где можно найти коды ошибок Win32? | Документы Майкрософт
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
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86735dae123d0fdedc59f4205af349b86cc6efd0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560451"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Где можно найти коды ошибок Win32?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [где по может выглядеть в копии коды ошибок Win32?](https://docs.microsoft.com/visualstudio/debugger/where-can-i-look-up-win32-error-codes-q).  
  
WINERROR.H в папке INCLUDE стандартного дистрибутива содержит определения кодов ошибок для функций Win32 API.  
  
 Можно выполнять поиск кода ошибки, введя код в **Watch** окна или **"Быстрая проверка"** диалоговое окно. Пример:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)



