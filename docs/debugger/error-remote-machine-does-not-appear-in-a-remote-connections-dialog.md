---
title: Удаленный компьютер не отображается в диалоговом окне удаленных подключений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be39d733b2e5fe83fa9f7e2241c7de06980bb583
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871374"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Ошибка: Удаленный компьютер не отображается в диалоговом окне удаленных подключений
Если удаленный компьютер не отображается в диалоговом окне "Удаленные подключения", проверьте указанные ниже наиболее вероятные причины.

 Если вы используете режим совместимости управляемого кода, обратитесь к документации по Visual Studio 2010: [Устранение неполадок удаленной отладки в Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100))

### <a name="common-causes-for-this-error"></a>Распространенные причины этой ошибки

- Удаленный компьютер находится в другой подсети. Чтобы устранить эту проблему, вручную введите имя или IP-адрес компьютера в окне "Описатель".

- Удаленный отладчик не запущен на удаленном компьютере. Чтобы устранить эту проблему, запустите удаленный отладчик.

- Брандмауэр блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте брандмауэр, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).

- Антивирусная программа блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте антивирусную программу, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)