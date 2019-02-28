---
title: 'Ошибка: Узел использует IP-адрес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 57790fce73c96a37c678f32cb76e332c28f73673
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696510"
---
# <a name="error-site-uses-ip-address"></a>Ошибка: веб-узел использует IP-адрес
Эта ошибка возникает, если в отладчике выполняется попытка автоматического присоединения к веб-приложению, которое использует IP-адрес. Это происходит при изменении в IIS параметра **идентификация веб-узла** на значение **определенный IP-адрес**.

 Для работы автопривязки необходимо создать проект с определенным IP-адресом вместо имени компьютера. В противном случае имя машины будет заменено отладчиком на имя "localhost". Это вызовет сбой отправки команды службам IIS.

### <a name="to-correct-this-error"></a>Исправление ошибки

1.  Используйте ручную привязку вместо автопривязки (в меню "Отладка" выберите пункт **Присоединение к процессу**).

     —или—

2.  Измените параметр **Идентификация веб-узла IIS**.

## <a name="see-also"></a>См. также раздел
- [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)