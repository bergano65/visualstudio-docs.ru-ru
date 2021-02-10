---
title: Средства для обнаружения экземпляров Visual Studio и управления ими
titleSuffix: ''
description: Сведения о средствах, с помощью которых можно обнаруживать экземпляры Visual Studio, установленные на клиентских компьютерах, и управлять ими.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: efd4091407d228a15cc80971d759e5371bddd3ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959263"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Средства для обнаружения экземпляров Visual Studio и управления ими

Имеется ряд средств, с помощью которых можно обнаруживать экземпляры Visual Studio, установленные на клиентских компьютерах, а также управлять ими.

## <a name="detecting-existing-visual-studio-instances"></a>Обнаружение существующих экземпляров Visual Studio

Мы предлагаем несколько средств, предназначенных для обнаружения установленных экземпляров Visual Studio на клиентских компьютерах и управления ими:

* [vswhere](https://github.com/microsoft/vswhere). Исполняемый файл, входящий в состав Visual Studio и доступный для отдельного распространения, который поможет вам найти расположение всех экземпляров Visual Studio на конкретном компьютере.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell). Скрипты PowerShell, которые позволяют определить установленные экземпляры Visual Studio с помощью API конфигурации установки.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples). Образцы на языках C# и C++, демонстрирующие применение API конфигурации установки для запроса существующей установки.

Кроме того, [API конфигурации установки](<xref:Microsoft.VisualStudio.Setup.Configuration>) реализует интерфейсы для разработчиков, которые хотят создавать свои собственные служебные программы для опроса экземпляров Visual Studio.

## <a name="using-vswhereexe"></a>С помощью vswhere.exe

`vswhere.exe` автоматически включается в состав Visual Studio (начиная с Visual Studio 2017 версии 15.2 и более поздних), либо его можно скачать на [странице выпусков vswhere](https://github.com/Microsoft/vswhere/releases). Используйте `vswhere -?`, чтобы получить информацию об этом средстве. Следующий пример команды выводит в формате JSON полный список выпусков Visual Studio, включая предыдущие и предварительные версии продукта:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Дополнительные сведения об установке Visual Studio 2017 см. в [архивах по установке Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Редактирование реестра для экземпляра Visual Studio

Параметры реестра для Visual Studio сохраняются в частном расположении, что позволяет устанавливать параллельно несколько экземпляров одной версии Visual Studio на одном компьютере.

Поскольку эти записи не хранятся в глобальном реестре, для изменения этих параметров с помощью редактора реестра используется отдельная процедура.

1. Если открыт любой экземпляр Visual Studio, закройте его.

1. Запустите среду `regedit.exe`.

1. Выберите узел `HKEY_LOCAL_MACHINE`.

1. В главном меню редактора реестра выберите пункты **Файл** > **Загрузить куст...** и файл частного реестра из папки **AppData\Local**. Пример:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` обозначает экземпляр Visual Studio, который вы хотите просмотреть.

Вам будет предложено предоставить имя используемого изолированного куста. После этого вы сможете просматривать параметры реестра, хранящиеся в созданном изолированном кусте.

> [!IMPORTANT]
> Прежде чем возвращаться к работе в Visual Studio, необходимо выгрузить созданный вами изолированный куст. Для этого выберите **Файл** > **Выгрузить куст** в главном меню редактора реестра. (Если этого не сделать, файл останется заблокированным и Visual Studio не сможет запуститься.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также раздел

* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
