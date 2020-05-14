---
title: Devenv Командно-линейные коммутаторы для развития VSPackage (ru) Документы Майкрософт
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712196"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Параметры командной строки devenv для разработки VSPackage

Visual Studio позволяет разработчикам автоматизировать задачи из `devenv.exe`командной строки при выполнении файла, который запускает Visual Studio IDE.

 Задачи включают в себя:

- Развертывание приложений в заранее разработанных конфигурациях за пределами IDE.

- Автоматические проекты построения с использованием предустановленных параметров сборки или конфигураций отладки.

- Загрузка IDE в определенных конфигурациях, все из-за пределов IDE. Вы также можете настроить IDE при запуске.

## <a name="guidelines-for-switches"></a>Руководящие принципы для коммутаторов

Документация Visual Studio описывает `devenv` переключатели командной строки пользовательского уровня. Для получения дополнительной [Devenv command-line switches](../ide/reference/devenv-command-line-switches.md)информации см. Инструмент `devenv` также поддерживает дополнительные коммутаторы командной строки, которые полезны при разработке, развертывании и отладке VSPackage.

| Переключатель командной строки | Описание |
|---------------------| - |
| `/ResetSkipPkgs` | Очищает все параметры загрузки, которые были добавлены пользователями, которые хотят избежать загрузки проблемных VSPackages, а затем запускает Visual Studio. Наличие тега SkipLoading отсчитывает загрузку VSPackage. Очистка тега повторно позволяет загрузки VSPackage.<br /><br /> У этого параметра нет аргументов. |
| `/RootSuffix` | Запускает Visual Studio с помощью альтернативного местоположения. Следующая команда выполняется ярлыком, созданным установщиком Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> В этом `exp` случае идентифицирует местоположение с определенным суффиксом (например, `10.0Exp` `10.0`вместо). Экспериментальный экземпляр позволяет отладить VSPackage отдельно от экземпляра Visual Studio, который вы используете для записи кода.<br /><br /> Этот переключатель может принимать любую строку, которая определяет место, которое вы создали с помощью VSRegEx.exe. Для получения дополнительной информации [см.](../extensibility/the-experimental-instance.md) |
| `/SafeMode` | Запускает Visual Studio в безопасном режиме, загружая только IDE по умолчанию и услуги. Коммутатор `/SafeMode` предотвращает загрузку всех сторонних VSPackages при запуске Visual Studio, обеспечивая стабильное выполнение.<br /><br /> У этого параметра нет аргументов. |
| `/Setup` | Силы Visual Studio объединить метаданные ресурсов, описывающие меню, панели инструментов и группы команд из всех доступных VSPackages. Эту команду можно запустить только в качестве администратора. <br /><br /> У этого параметра нет аргументов. Команда `devenv /Setup` обычно выдается в качестве последнего этапа процесса установки. Использование коммутатора `/Setup` не начинается с IDE.|
| `/Splash` | Показывает экран всплеска Visual Studio, как обычно, а затем показывает окно сообщений, прежде чем показывать основной IDE. Коробка сообщений позволяет изучить экран всплеска (например, проверить значок продукта VSPackage).<br /><br /> У этого параметра нет аргументов. |

## <a name="see-also"></a>См. также

- [Добавление коммутаторов командной строки](../extensibility/adding-command-line-switches.md)
- [Параметры командной строки для Devenv](../ide/reference/devenv-command-line-switches.md)
