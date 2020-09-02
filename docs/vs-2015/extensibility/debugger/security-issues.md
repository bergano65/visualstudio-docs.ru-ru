---
title: Проблемы безопасности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704426"
---
# <a name="security-issues"></a>Проблемы с безопасностью
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Для отладки программы с помощью Visual Studio необходимы только те же разрешения, что и разработчику, который должен запустить программу. Сюда входит удаленная отладка для большинства ситуаций (в некоторых ситуациях для других служб, таких как служба IIS, может потребоваться более высокий уровень разрешений).  
  
 Пока выполняется Visual Studio, диспетчер отладки процессов (PDM) отслеживает процессы отладки на локальном компьютере. Удаленно, программа с именем msvsmon.exe запускается разработчиком для выполнения удаленной отладки и делает PDM доступным. (Обратите внимание, что msvsmon.exe не является службой, и ее необходимо запустить вручную, чтобы включить удаленную отладку на этом компьютере.) Если Visual Studio (или msvsmon.exe) не запущена, процессы для отладки не отправляются.  
  
 Это означает, что разработчик может выполнять отладку программ, которые он запустил, без специальных разрешений. Разработчик может даже выполнять отладку процессов, запущенных другим пользователем, если он является членом той же группы безопасности. Чтобы включить удаленную отладку, необходимо только скопировать необходимые файлы на удаленный компьютер и запустить msvsmon.exe (Дополнительные сведения см. [в разделе настройка удаленные средства на устройстве](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) ).  
  
## <a name="see-also"></a>См. также:  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [Диспетчер отладки процессов](../../extensibility/debugger/process-debug-manager.md)   
 [Настройка инструментов удаленной отладки в устройстве](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
