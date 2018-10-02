---
title: Проблемы безопасности | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0459f7e91fbced71dda0bb401ffe056b5cd49f52
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558705"
---
# <a name="security-issues"></a>Проблемы безопасности
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [проблемы безопасности](https://docs.microsoft.com/visualstudio/extensibility/debugger/security-issues).  
  
Чтобы отладить программу, с помощью Visual Studio, только разрешения, необходимые являются те же, что разработчику необходимо запустить программу. Это включает в себя удаленной отладки для большинства ситуаций (некоторых ситуаций, связанных с других служб, таких как службы IIS, может потребоваться более высокий уровень разрешений).  
  
 Во время работы Visual Studio, диспетчер отладки процессов (PDM) отслеживает отладки процессов на локальном компьютере. Удаленно программу под названием msvsmon.exe запускается разработчиком для обработки удаленной отладки и предоставления PDM. (Обратите внимание, что msvsmon.exe не является службой и позволяет включить удаленную отладку на этом компьютере должна быть запущена вручную.) Когда Visual Studio (или msvsmon.exe) не запущена, процессы не отслеживаются для отладки.  
  
 Это означает, что разработчик можно отлаживать программы, в которой он или она начали с помощью специальных разрешений. Разработчик может даже осуществляйте отладку процессов, запущенных другим пользователем, если что-то другой человек входит в ту же группу безопасности. И позволяет включить удаленную отладку, он необходим только для копирования необходимых файлов на удаленный машинного и запустите msvsmon.exe (см. в разделе [задать удаленных инструментов на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) подробности).  
  
## <a name="see-also"></a>См. также  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [Диспетчер отладки процессов](../../extensibility/debugger/process-debug-manager.md)   
 [Настройка инструментов удаленной отладки в устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)

