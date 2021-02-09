---
title: Руководство. Установка распространяемого пакета среды выполнения Office Инструменты Visual Studio
description: Узнайте, как можно установить распространяемый пакет средств Microsoft Visual Studio 2010 для Office Runtime.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75dc5b2f3f207603320a773ebd71f5d6d3f81b8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918622"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Руководство. Установка распространяемого пакета среды выполнения Office Инструменты Visual Studio
  Среда выполнения средств Visual Studio 2010 для Office должна быть установлена на каждом компьютере, где работают решения, созданные с помощью средств разработчика Microsoft Office в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Она устанавливается автоматически при установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и Microsoft Office. Дополнительные сведения см. в статье [инструменты Visual Studio для сценариев установки среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 В указанных ниже ситуациях следуйте описанных инструкциям по установке вручную.

- Установите на сервер [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Допустим, вы хотите использовать класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, чтобы управлять на сервере решениями на уровне документов.

- Установите среду выполнения на компьютер, где уже установлены все остальные компоненты, необходимые для решений Office.

    > [!NOTE]
    > Для установки .NET Framework и [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] на компьютер разработчика требуются права администратора.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Установка среды выполнения Visual Studio Tools для Office

1. Установите [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.

    - Сведения о загрузке см [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . в разделе [Microsoft .NET Framework 4 (веб-установщик)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Чтобы скачать [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] , см. раздел [клиентский профиль Microsoft .NET Framework 4 (веб-установщик)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Чтобы скачать [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , см. статью [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Запустите *vstor_redist.exe* , чтобы установить [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     Эти файлы установки можно загрузить из [среды выполнения Visual Studio 2010 Tools for Office](https://www.microsoft.com/download/details.aspx?id=56961). Предварительные требования [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] совпадают с предварительными требованиями платформы .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] включает языковые пакеты. Если при установке Windows был выбран не английский язык, сообщения среды выполнения будут отображаться на языке, выбранном для Windows. Точно так же, если конечные пользователи установят [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и запустят ваши решения в системах Windows, настроенных не на английский язык, сообщения среды выполнения будут отображаться на языке Windows. В некоторых случаях могут потребоваться дополнительные языковые пакеты. Например, могут потребоваться дополнительные языковые пакеты, если в вашей копии Windows используется более одного языкового параметра, или если вы уже установили на другой язык [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Языковые пакеты можно найти в [Microsoft Visual Studio средств 2010 для языкового пакета Microsoft Office системы (среда выполнения версии 4,0)](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>См. также раздел
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Как настроить компьютер для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
