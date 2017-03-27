---
title: "Руководство администратора Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 69ac1327fa9233bf0ecc18be5e7d2f2a4f82b3b0
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Руководство администратора Visual Studio 2017

Visual Studio можно развертывать в сети, если каждый конечный компьютер отвечает [минимальным требованиям для установки](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Чтобы создать общую сетевую папку, запустите файл установки с параметром --layout, как описано в разделе [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md), а затем скопируйте его с локального компьютера в общую сетевую папку.   

 Обратите внимание, что установки из общей сетевой папки "запоминают" исходное расположение, из которого они выполнялись. Это означает, что при восстановлении клиентского компьютера может потребоваться вернуться к сетевой папке, из которой клиент был установлен изначально. В связи с этим необходимо внимательно отнестись к выбору сетевых расположений, которые должны соответствовать времени существования клиентов Visual Studio 2017 в вашей организации.

## <a name="tools"></a>Инструменты

 У нас есть несколько средств, которые помогут вам управлять установками Visual Studio.

* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples). Это примеры на языках C# и C++, которые помогут пользователям запрашивать экземпляры VS на своих компьютерах.
* [VSWhere](https://github.com/microsoft/vswhere). Исполняемый EXE-файл на C++, который помогает найти основные средства Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell). Мощные скрипты PowerShell для распространенных задач администрирования, связанных с установкой.


## <a name="see-also"></a>См. также
* [Установка Visual Studio 2017](install-visual-studio.md)
* [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Использование идентификаторов рабочих нагрузок и компонентов Visual Studio для настройки автономной установки](workload-and-component-ids.md)
* [Как сообщить о проблеме с Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

