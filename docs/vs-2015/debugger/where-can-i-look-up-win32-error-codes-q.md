---
title: Где можно найти коды ошибок Win32? | Документы Майкрософт
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
ms.openlocfilehash: ce5cc450c05ee759d4d65e22394c6ef814b0a872
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206002"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Где можно найти коды ошибок Win32?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WINERROR.H в папке INCLUDE стандартного дистрибутива содержит определения кодов ошибок для функций Win32 API.  
  
 Можно выполнять поиск кода ошибки, введя код в **Watch** окна или **"Быстрая проверка"** диалоговое окно. Пример:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)



