---
title: "Настройка начальной страницы в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 178c20c9c4c3af8f5252e70ca603cdf8f8335e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>Настройка начальной страницы в Visual Studio
Существует несколько способов настройки начальной страницы Visual Studio: например, для этого можно использовать диалоговое окно **Открытие проекта** или открыть решение, загруженное последним. Также можно отобразить настраиваемую начальную страницу, т. е. страницу XAML Windows Presentation Foundation (WPF), которая открывается в окне инструментов и может использоваться для выполнения внутренних команд Visual Studio.  

## <a name="customize-the-default-start-page"></a>Настройка начальной страницы по умолчанию  

1.  В строке меню выберите **Сервис**, **Параметры**.  

2.  Разверните меню **Среда** и выберите **Запуск**.  

3.  В списке **При запуске** выберите элемент, который требуется настроить.  

## <a name="show-a-custom-start-page"></a>Отображение настраиваемой начальной страницы  

1.  Установите настраиваемую начальную страницу одним из следующих способов:  

    -   Установите данную страницу из [галереи Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), с другого веб-сайта или со страницы своей локальной интрасети.  

        Откройте файл VSIX, содержащий настраиваемую начальную страницу, или скопируйте и вставьте файлы начальной страницы в папку **%USERPROFILE% \Мои документы\Visual Studio 2017\StartPages** на компьютере.  

    -   Создайте собственную начальную страницу, если на вашем компьютере установлен пакет SDK для Visual Studio.  

         См. раздел [Создание настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md).  

2.  В строке меню выберите **Сервис**, **Параметры**.  

3.  Разверните меню **Среда** и выберите **Запуск**.  

4.  В списке **Настроить начальную страницу** выберите нужную страницу.  

> [!NOTE]
>  Если ошибка в настраиваемой начальной странице вызывает сбой Visual Studio, можно запустить Visual Studio в безопасном режиме, а затем настроить использование начальной страницы по умолчанию. См. раздел [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  

## <a name="see-also"></a>См. также  
 [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md)   
