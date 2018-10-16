---
title: 'Предупреждение системы безопасности: Присоединение к процессу, который принадлежит недоверенному пользователю может быть опасно. Если приведенные ниже выглядит подозрительно, или вы не уверены, не присоединяться к процессу | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2018
ms.locfileid: "34178012"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Предупреждение системы безопасности: Присоединение к процессу, который принадлежит недоверенному пользователю может быть опасно. Если приведенные ниже выглядит подозрительно, или вы не уверены, не присоединяться к процессу
Это диалоговое окно с предупреждением появляется непосредственно перед присоединением к процессу, который содержит частично доверенный код или принадлежит недоверенному пользователю. Недоверенный процесс, содержащий вредоносный код, может нанести вред компьютеру, на котором выполняется отладка. Если имеется причина не доверять процессу, то следует нажать кнопку **отменить** для предотвращения отладки.  
  
 Чтобы отключить это предупреждение при отладке надежного сценария, закройте Visual Studio и присвойте значение этого раздела реестра 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, а затем перезапустите Visual Studio. Завершив отладку данного сценария, вновь верните значение "0" и перезапустите Visual Studio.  
  
 К числу "доверенных пользователей" относится ваша учетная запись, а также набор стандартных пользователей, которые обычно определены на компьютерах с установленной платформой .NET Framework, например: `aspnet`, `localsystem`, `networkservice` и `localservice`.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 name  
 Имя сборки, запрашиваемой для отладки  
  
 Пользовательская  
 Текущий пользователь  
  
 Attach  
 Нажмите, чтобы продолжить отладку путем присоединения.  
  
 Не присоединяться  
 Не присоединяться к процессу.  
  
## <a name="see-also"></a>См. также  
 [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)