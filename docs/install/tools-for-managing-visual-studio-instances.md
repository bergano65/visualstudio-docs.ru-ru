---
title: "Средства для обнаружения экземпляров Visual Studio и управления ими | Документация Майкрософт"
description: "{{ЗАПОЛНИТЕЛЬ}}"
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 1e81071d8a67fd5b8c38bcf87629604efe6fa4a5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---

# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Средства для обнаружения экземпляров Visual Studio и управления ими

## <a name="detecting-existing-visual-studio-instances"></a>Обнаружение существующих экземпляров Visual Studio
Мы предлагаем несколько средств, предназначенных для обнаружения установленных экземпляров Visual Studio на клиентских компьютерах и управления ими:

* [VSWhere](https://github.com/microsoft/vswhere). Исполняемый файл, входящий в состав Visual Studio и доступный для отдельного распространения, который поможет вам найти расположение всех экземпляров Visual Studio на конкретном компьютере.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell). Скрипты PowerShell, которые позволяют определить установленные экземпляры Visual Studio с помощью API конфигурации установки.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples). Образцы на языках C# и C++, демонстрирующие применение API конфигурации установки для запроса существующей установки.

Кроме того, [API конфигурации установки](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) реализует интерфейсы для разработчиков, которые хотят создавать свои собственные служебные программы для опроса экземпляров Visual Studio.

## <a name="using-vswhereexe"></a>С помощью vswhere.exe
`vswhere.exe` по умолчанию входит в состав Visual Studio 2017, начиная с версии 15.2. Также его можно скачать отдельно на [странице выпусков](https://github.com/Microsoft/vswhere/releases). Используйте `vswhere -?`, чтобы получить информацию об этом средстве. Следующий пример команды выводит в формате JSON полный список выпусков Visual Studio, включая устаревшие версии продукта и предварительные версии:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Дополнительные сведения об установке Visual Studio 2017 г. в [статьях блога Хита Стюарта (Heath Stewart)](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Редактирование реестра для экземпляра Visual Studio
Параметры реестра для Visual Studio 2017 сохраняются в частном хранилище, что позволяет устанавливать параллельно несколько экземпляров одной версии Visual Studio на одном компьютере.

Поскольку эти записи не хранятся в глобальном реестре, для изменения этих параметров с помощью редактора реестра используется отдельная процедура.

1. Если открыт любой экземпляр Visual Studio 2017, закройте его.
2. Запустите `regedit.exe`.
3. Выберите узел `HKEY_LOCAL_MACHINE`.
4. В главном меню редактора реестра выберите пункты **Файл -> Загрузить куст...** и выберите файл частного реестра из папки **AppData\Local**. Пример:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` обозначает экземпляр Visual Studio, который вы хотите просмотреть.

Вам будет предложено предоставить имя используемого изолированного куста. После этого вы сможете просматривать параметры реестра, хранящиеся в созданном изолированном кусте.

> [!IMPORTANT]
> Прежде чем возвращаться к работе в Visual Studio, необходимо выгрузить созданный вами изолированный куст. Для этого выберите команду "Файл" -> "Выгрузить куст" в главном меню редактора реестра. (Если этого не сделать, файл останется заблокированным и Visual Studio не сможет запуститься.)

