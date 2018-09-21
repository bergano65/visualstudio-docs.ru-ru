---
title: Обнаружение Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 08/21/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65b0b8dfcc42cfcf80fc24f0c844469b77734e9c
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495392"
---
# <a name="locate-visual-studio"></a>Найдите Visual Studio

Начиная с Visual Studio 2017, можно установить несколько экземпляров одной версии или даже edition. Это полезно в тех случаях, когда требуется просмотреть новые функциональные возможности на компьютере разработки основной сохраняя предыдущей установки. Из-за этих изменений нет значения переменной или раздела реестра единой среде, которые можно использовать для поиска экземпляра. Вместо этого можно использовать [запроса COM API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) для поиска экземпляров на основе критериев, которые важны для вашего расширения.

Это быстрый, доступный только для чтения API с помощью пакетов NuGet, доступных для машинного и управляемого кода.

| Код | Пакет |
| ---- | --- |
| машинный код; | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Управляемый | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Можно найти один экземпляр, заданный путь или текущего процесса или перечислить все экземпляры. См. в разделе [наши примеры](https://github.com/Microsoft/vs-setup-samples) полные примеры того, как найти Visual Studio.

## <a name="tools"></a>Инструменты

Чтобы найти Visual Studio и другие инструменты в сред построения, скрипты PowerShell, установщики и дополнительные сценарии, существует ряд средств с открытым исходным кодом можно использовать непосредственно или повторно распространить вместе с вашим собственным сценариям.

| Проект | Описание |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Один файл исполняемый файл машинного кода для поиска экземпляров, удовлетворяющие критериям, например выпуска или предварительной версии, что продукт установлен и установлены какие рабочие нагрузки. Также поддерживает поиск Visual Studio 2010 и более поздних версий, хотя меньше возвращаются сведения, для Visual Studio 2017 и более поздних. См. в разделе [вики-сайте](https://github.com/Microsoft/vswhere/wiki) примеры. |
| [Командлеты VSSetup](https://github.com/Microsoft/vssetup.powershell) | Поддержка командлетов PowerShell 2.0 и более поздних версий, которые возвращают ценной информации как объекты, можно использовать для поиска экземпляров с учетом таким же образом _vswhere_ и для обнаружения свойств еще больше об экземплярах. См. в разделе [вики-сайте](https://github.com/Microsoft/vssetup.powershell/wiki) примеры. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Автоматически находит _установщик VSIX_ и передает командной строки для установки **.vsix* файл. Эту функцию можно использовать в установщики, которые не имеют прямой поддержки для запроса API-интерфейсы. См. в разделе [вики-сайте](https://github.com/Microsoft/vsixbootstrapper/wiki) примеры. |

## <a name="see-also"></a>См. также

* [Изменения в программе установки Visual Studio 2017](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup/)
