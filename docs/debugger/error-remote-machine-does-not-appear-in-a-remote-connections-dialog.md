---
title: 'Ошибка: Удаленный компьютер не отображается в диалоговом окне удаленных подключений | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: dd194bc26574e8004894a72ce29d753cabf66a21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850800"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Ошибка: Удаленный компьютер не отображается в диалоговом окне удаленных подключений
Если удаленный компьютер не отображается в диалоговом окне "Удаленные подключения", проверьте указанные ниже наиболее вероятные причины.

 Если вы используете режим совместимости управляемого кода, см. в документации Visual Studio 2010: [Устранение неполадок удаленной отладки — Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Распространенные причины этой ошибки

- Удаленный компьютер находится в другой подсети. Чтобы устранить эту проблему, вручную введите имя или IP-адрес компьютера в окне "Описатель".

- Удаленный отладчик не запущен на удаленном компьютере. Чтобы устранить эту проблему, запустите удаленный отладчик.

- Брандмауэр блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте брандмауэр, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).

- Антивирусная программа блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте антивирусную программу, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)