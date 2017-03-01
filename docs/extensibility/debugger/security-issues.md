---
title: "Проблемы безопасности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>Проблемы безопасности
Для отладки программы с помощью Visual Studio, только необходимые разрешения являются те же, что разработчику необходимо запустить программу. Это включает удаленную отладку в большинстве ситуаций (некоторых ситуаций, связанных с другими службами, например служб IIS, может потребоваться более высокий уровень разрешений).  
  
 Пока выполняется Visual Studio, диспетчер отладки процессов (PDM) отслеживает отладки процессов на локальном компьютере. Удаленно разработчиком для удаленной отладки и предоставления PDM запускается программа с именем msvsmon.exe. (Обратите внимание, что msvsmon.exe не является службой и позволяет включить удаленную отладку на этом компьютере должна быть запущена вручную.) Когда Visual Studio (или msvsmon.exe) не запущена, процессы не отслеживаются для отладки.  
  
 Это означает, что разработчик можно отлаживать программы, которой он начал без специальных разрешений. Разработчик может даже отладку процессов, запущенных другим пользователем, если, другой пользователь входит в группу безопасности. И для удаленной отладки, это необходимо только для копирования необходимых файлов для удаленного компьютера и запустите msvsmon.exe (см. [удаленной отладки](../../debugger/remote-debugging.md) Дополнительные сведения).  
  
## <a name="see-also"></a>См. также  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [Диспетчер процессов отладки](../../extensibility/debugger/process-debug-manager.md)   
 [Удаленная отладка](../../debugger/remote-debugging.md)
