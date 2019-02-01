---
title: Предупреждение системы безопасности. Подключение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если вы не уверены, ниже сведения, не присоединяться к процессу | Документация Майкрософт
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17511c5f89ca40cc002a80da955df10c8773b97c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952188"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Предупреждение системы безопасности. Подключение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу
Это диалоговое окно с предупреждением появляется непосредственно перед присоединением к процессу, который содержит частично доверенный код или принадлежит недоверенному пользователю. Недоверенный процесс, содержащий вредоносный код, может нанести вред компьютеру, на котором выполняется отладка. Если имеется причина не доверять процессу, следует нажать кнопку **Отмена** для предотвращения отладки.  
  
 Чтобы отключить это предупреждение при отладке надежного сценария, закройте Visual Studio и установите значение параметра реестра 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, а затем перезапустите Visual Studio. Завершив отладку данного сценария, вновь верните значение "0" и перезапустите Visual Studio.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Подключение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)