---
title: Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если вы не уверены, ниже сведения, не присоединяться к процессу | Документация Майкрософт
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
- vs.debug.attachsecuritywarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b856ac3a61d8af72d78546948bbe4ab780e9512e
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592508"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [предупреждение системы безопасности: присоединение к процессу, принадлежит недоверенному пользователю не может быть опасно. Если вы не уверены, ниже сведения, не присоединяться к процессу](https://docs.microsoft.com/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process).  
  
Это диалоговое окно с предупреждением появляется непосредственно перед присоединением к процессу, который содержит частично доверенный код или принадлежит недоверенному пользователю. Недоверенный процесс, содержащий вредоносный код, может нанести вред компьютеру, на котором выполняется отладка. Если у вас есть причина не доверять процессу, то следует нажать кнопку **отменить** для предотвращения отладки.  
  
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
  
## <a name="see-also"></a>См. также  
 [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)



