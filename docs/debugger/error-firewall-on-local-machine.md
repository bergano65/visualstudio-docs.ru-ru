---
title: 'Ошибка: Брандмауэр на локальном компьютере | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1781fef79dc9d80bae6a0484788298324e8bbd52
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963740"
---
# <a name="error-firewall-on-local-machine"></a>Ошибка: брандмауэр на локальном компьютере
Брандмауэр подключения к интернету на локальном компьютере, с которого запускается Visual Studio, не настроен так, чтобы была доступна удаленная отладка. Для удаленной отладки управляемого или машинного кода с транспортом по умолчанию, порт TCP 135 должен быть открыт для трафика DCOM. Необходимо открыть общий доступ к файлам и принтерам, и файл devenv.exe должен быть добавлен в список исключений. Возможно также потребуется открыть некоторые порты IPSec.  
  
 Дополнительные сведения см. в разделе [удаленной отладки](../debugger/remote-debugging.md).