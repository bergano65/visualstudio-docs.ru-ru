---
title: "Руководство администратора Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/12/2017
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
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 91fb897e0bf124234484c3aada08ac57c4be1923
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017-rc"></a>Руководство администратора для версии-кандидата Visual Studio 2017

Visual Studio можно развертывать в сети, если каждый конечный компьютер отвечает [минимальным требованиям для установки](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Вы можете создать общую сетевую папку, запустив файл установки с параметром --layout, как описано в разделе [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md), а затем скопировав его с локального компьютера в общую сетевую папку.   

 Обратите внимание, что установки из общей сетевой папки "запоминают" исходное расположение, из которого они выполнялись. Это означает, что при восстановлении клиентского компьютера может потребоваться вернуться к сетевой папке, из которой клиент был установлен изначально. В связи с этим необходимо внимательно отнестись к выбору сетевых расположений, которые должны соответствовать времени существования клиентов Visual Studio 2017 в вашей организации.  

 > [!IMPORTANT]
 > Хотя версию-кандидат Visual Studio 2017 в общем можно использовать в рабочей среде, рабочие нагрузки и компоненты, которые в пользовательском интерфейсе установки доступны в режиме предварительной версии, в рабочей среде не поддерживаются.

## <a name="see-also"></a>См. также
* [Установка версии-кандидата Visual Studio 2017](install-visual-studio.md)
* [Использование параметров командной строки для установки версии-кандидата Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Создание автономной установки версии-кандидата Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Как сообщить о проблеме с версией-кандидатом Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

