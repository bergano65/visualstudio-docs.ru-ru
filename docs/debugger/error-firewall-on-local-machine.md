---
title: 'Ошибка: Брандмауэр на локальном компьютере | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e85c97d5950f71d9552bba944450603e47a5ab49
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="error-firewall-on-local-machine"></a>Ошибка: брандмауэр на локальном компьютере
Брандмауэр подключения к интернету на локальном компьютере, с которого запускается Visual Studio, не настроен так, чтобы была доступна удаленная отладка. Для удаленной отладки управляемого или машинного кода с транспортом по умолчанию, порт TCP 135 должен быть открыт для трафика DCOM. Необходимо открыть общий доступ к файлам и принтерам, и файл devenv.exe должен быть добавлен в список исключений. Возможно также потребуется открыть некоторые порты IPSec.  
  
 Дополнительные сведения см. в разделе [удаленной отладки](../debugger/remote-debugging.md).