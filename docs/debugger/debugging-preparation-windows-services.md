---
title: Подготовка к отладке служб Windows | Документация Майкрософт
description: Подготовка к отладке служб Windows в Visual Studio. Эти службы представляют собой программы, выполняемые в фоновом режиме под управлением Windows.
ms.custom: SEO-VS-2020, seodec18
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdf82b708440cb3201c5d05bd936c7f7d9c30729
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872398"
---
# <a name="debugging-preparation-windows-services"></a>Подготовка к отладке: службы Windows
Служба Windows – это программа, которая выполнятся в фоновом режиме в Microsoft Windows. Примерами таких служб является служба Telnet и служба времени Windows, изменяющая часы, отображаемые на рабочем столе. Служба Windows не может быть запущена из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; ее необходимо запускать из диспетчера управления службами. Дополнительные сведения см. в разделах [Создание служб Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [Отладка приложений служб Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) и [Приложения служб Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>См. также
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Практическое руководство. отладка метода OnStart](../debugger/how-to-debug-the-onstart-method.md)