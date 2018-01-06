---
title: "Обнаружение Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 08/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5623ea382266fdbcd59bbe57b71522a7a1f4a31e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="locating-visual-studio"></a>Обнаружение Visual Studio

Начиная с Visual Studio 2017 г., можно установить несколько экземпляров одной версии или даже выпуска. Это полезно в тех случаях, когда требуется просмотреть новые функциональные возможности на компьютере разработки основной сохраняя предыдущую установку. После внесения этих изменений нет, можно использовать, чтобы найти экземпляр значения переменной или раздела реестра единую среду. Вместо этого можно использовать [запроса COM API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) для поиска экземпляров на основе критериев, которые важны для вашего расширения.

Это — это быстрый, только для чтения API с пакетами NuGet для машинного и управляемого кода.

| Код | Пакет |
| ---- | --- |
| машинный код; | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Управляемый | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Найдите один экземпляр, заданный путь или текущего процесса или перечислить все экземпляры. В разделе [наши примеры](https://github.com/Microsoft/vs-setup-samples) полные примеры того, как найти Visual Studio.

## <a name="tools"></a>Инструменты

Чтобы найти Visual Studio и другие инструменты в среды сборки c, скрипты PowerShell, установщики и другие сценарии, у нас есть ряд средств открытым исходным кодом можно использовать непосредственно или повторно распространить вместе с собственных сценариев.

| Проект | Описание: |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Один файл собственного исполняемый файл, чтобы найти экземпляры, соответствующие критериям, например выпуска или предварительной версии, что продукт установлен и устанавливаются, рабочая нагрузка. Также поддерживает поиск Visual Studio 2010 и более поздних версиях на то, что меньше возвращаются сведения, для Visual Studio 2017 г. и более поздних. В разделе [вики-сайте](https://github.com/Microsoft/vswhere/wiki) примеры. |
| [Командлеты VSSetup](https://github.com/Microsoft/vssetup.powershell) | Поддерживаемые командлеты PowerShell 2.0 и более поздних, возвращающие подробные сведения как объекты можно использовать для поиска экземпляров на основе одного условия как _vswhere_ и для обнаружения свойств еще больше об экземплярах. В разделе [вики-сайте](https://github.com/Microsoft/vssetup.powershell/wiki) примеры. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Автоматически находит _VSIXInstaller_ и передает через командной строки для установки _*.vsix_ файла. Это может быть полезно в установщики, у которых нет непосредственной поддержки API-интерфейсы запроса. В разделе [вики-сайте](https://github.com/Microsoft/vsixbootstrapper/wiki) примеры. |

## <a name="see-also"></a>См. также

* [Изменения в 2017 г. программа установки Visual Studio](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
