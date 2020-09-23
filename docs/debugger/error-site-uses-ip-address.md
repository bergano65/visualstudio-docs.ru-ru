---
title: Сайт использует IP-адрес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b869a536ca3445069d9caf84eb862e407dfbe6dc
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852541"
---
# <a name="error-site-uses-ip-address"></a>Ошибка: веб-узел использует IP-адрес
Эта ошибка возникает, если в отладчике выполняется попытка автоматического присоединения к веб-приложению, которое использует IP-адрес. Это происходит при изменении в IIS параметра **идентификация веб-узла** на значение **определенный IP-адрес**.

 Для работы автопривязки необходимо создать проект с определенным IP-адресом вместо имени компьютера. В противном случае имя машины будет заменено отладчиком на имя "localhost". Это вызовет сбой отправки команды службам IIS.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Используйте ручную привязку вместо автопривязки (в меню "Отладка" выберите пункт **Присоединение к процессу**).

     —или—

2. Измените параметр **Идентификация веб-узла IIS**.

## <a name="see-also"></a>См. также
- [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)