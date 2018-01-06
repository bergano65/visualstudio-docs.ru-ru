---
title: "Проблемы безопасности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 753f916d148675afd7313afc8673232f22280b7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="security-issues"></a>Проблемы безопасности
Для отладки программы, с помощью Visual Studio, только разрешения, необходимые являются теми же самыми элементами разработчику необходимо запустить программу. Сюда входят удаленной отладки в большинстве ситуаций (иногда с участием других служб, таких как службы IIS, может потребоваться более высокий уровень разрешений).  
  
 Пока выполняется Visual Studio, диспетчер отладочной процесса (PDM) отслеживает отладки процессов на локальном компьютере. Удаленно программу, которая называется msvsmon.exe запускается разработчиком для обработки удаленной отладки и сделать доступным PDM. (Обратите внимание, что msvsmon.exe, не является службой и позволяет включить удаленную отладку на этом компьютере должна быть запущена вручную.) Если Visual Studio (или msvsmon.exe) не запущена, процессы не отслеживаются для отладки.  
  
 Это означает, что разработчик можно отлаживать программы, которые он или она запущена без специальных разрешений. Разработчик может даже отладку процессов, запущенных другим пользователем, если у другого пользователя входит в группу безопасности. И для удаленной отладки, необходимо только для копирования необходимых файлов для удаленного компьютера и запустить msvsmon.exe (см. [удаленной отладки](../../debugger/remote-debugging.md) Дополнительные сведения).  
  
## <a name="see-also"></a>См. также  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [Диспетчер процессов отладки](../../extensibility/debugger/process-debug-manager.md)   
 [Удаленная отладка](../../debugger/remote-debugging.md)