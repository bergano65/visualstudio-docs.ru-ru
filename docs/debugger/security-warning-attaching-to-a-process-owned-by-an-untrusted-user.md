---
title: Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующая информация выглядит подозрительно или вы не уверены, не присоединитесь к этому процессу | Документация Майкрософт
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
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729778"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу
Это диалоговое окно с предупреждением появляется непосредственно перед присоединением к процессу, который содержит частично доверенный код или принадлежит недоверенному пользователю. Недоверенный процесс, содержащий вредоносный код, может нанести вред компьютеру, на котором выполняется отладка. Если имеется причина не доверять процессу, следует нажать кнопку **Отмена** для предотвращения отладки.

 Чтобы отключить это предупреждение при отладке допустимого сценария, закройте Visual Studio и присвойте этому разделу реестра значение 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, а затем перезапустите Visual Studio. Завершив отладку данного сценария, вновь верните значение "0" и перезапустите Visual Studio.

 К числу "доверенных пользователей" относится ваша учетная запись, а также набор стандартных пользователей, которые обычно определены на компьютерах с установленной платформой .NET Framework, например: `aspnet`, `localsystem`, `networkservice` и `localservice`.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 Имя имени сборки, запрошенной для отладки

 Текущий пользователь пользователя

 Подключить нажмите, чтобы продолжить отладку путем присоединения

 Не присоединяться к процессу

## <a name="see-also"></a>См. также
- [Подключение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Безопасность отладчика](../debugger/debugger-security.md)