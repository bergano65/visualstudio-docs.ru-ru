---
title: Настройка начальной страницы для Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ece49968c4a887e89f91feb83fae3de23aa2c282
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211488"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Настройка начальной страницы в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Существует несколько способов настройки начальной страницы Visual Studio: например, для этого можно использовать диалоговое окно **Открытие проекта** или открыть решение, загруженное последним. Также можно отобразить настраиваемую начальную страницу, т. е. страницу XAML Windows Presentation Foundation (WPF), которая открывается в окне инструментов и может использоваться для выполнения внутренних команд Visual Studio.  
  
## <a name="customizing-the-default-start-page"></a>Настройка начальной страницы по умолчанию  
  
1.  В строке меню выберите **Сервис**, **Параметры**.  
  
2.  Разверните меню **Среда** и выберите **Запуск**.  
  
3.  В списке **При запуске** выберите элемент, который требуется настроить.  
  
## <a name="show-a-custom-start-page"></a>Отображение настраиваемой начальной страницы  
  
1.  Установите настраиваемую начальную страницу одним из следующих способов:  
  
    -   Установите данную страницу из [галереи Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), с другого веб-сайта или со страницы своей локальной интрасети.  
  
        > [!NOTE]
        >  Если вы предпочитаете страницу, предназначенную для более ранней версии Visual Studio, то можете обновить ее при помощи пакета SDK для Visual Studio. См. в разделе [как: обновление настраиваемой начальной страницы Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
         Откройте VSIX-файл, содержащий настраиваемую начальную страницу, или скопируйте и вставьте файлы начальной страницы в **% USERPROFILE % Мои \My Documents\Visual Studio 2015\StartPages** папку на своем компьютере.  
  
    -   Создайте собственную начальную страницу, если на вашем компьютере установлен пакет SDK для Visual Studio.  
  
         См. в разделе [создание собственной начальной страницы](../misc/creating-your-own-start-page.md).  
  
2.  В строке меню выберите **Сервис**, **Параметры**.  
  
3.  Разверните меню **Среда** и выберите **Запуск**.  
  
4.  В списке **Настроить начальную страницу** выберите нужную страницу.  
  
> [!NOTE]
>  Если ошибка в настраиваемой начальной странице вызывает сбой Visual Studio, можно запустить Visual Studio в безопасном режиме, а затем настроить использование начальной страницы по умолчанию. См. раздел [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Создание начальной страницы](../misc/creating-your-own-start-page.md)



