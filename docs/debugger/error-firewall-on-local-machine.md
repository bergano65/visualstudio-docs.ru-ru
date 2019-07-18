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
ms.openlocfilehash: 87a1813410a092ced335f37b9df4cf6547ca1cc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851046"
---
# <a name="error-firewall-on-local-machine"></a>Ошибка: брандмауэр на локальном компьютере
Брандмауэр подключения к интернету на локальном компьютере, с которого запускается Visual Studio, не настроен так, чтобы была доступна удаленная отладка. Для удаленной отладки управляемого или машинного кода с транспортом по умолчанию, порт TCP 135 должен быть открыт для трафика DCOM. Необходимо открыть общий доступ к файлам и принтерам, и файл devenv.exe должен быть добавлен в список исключений. Возможно также потребуется открыть некоторые порты IPSec.

 Дополнительные сведения см. в разделе [удаленной отладки](../debugger/remote-debugging.md).