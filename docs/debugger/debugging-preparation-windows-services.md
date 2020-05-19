---
title: Подготовка к отладке служб Windows | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3161f6d2c328e8e33dd82ed206aa8aa20e654cc9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738090"
---
# <a name="debugging-preparation-windows-services"></a>Подготовка к отладке: службы Windows
Служба Windows – это программа, которая выполнятся в фоновом режиме в Microsoft Windows. Примерами таких служб является служба Telnet и служба времени Windows, изменяющая часы, отображаемые на рабочем столе. Служба Windows не может быть запущена из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; ее необходимо запускать из диспетчера управления службами. Дополнительные сведения см. в разделах [Создание служб Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [Отладка приложений служб Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) и [Приложения служб Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>См. также
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Практическое руководство. отладка метода OnStart](../debugger/how-to-debug-the-onstart-method.md)