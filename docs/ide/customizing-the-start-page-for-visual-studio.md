---
title: "Настройка начальной страницы в Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.startpage"
  - "VS.StartPage.HowDoI"
  - "vs.ToolsOptionsPages.Startup"
helpviewer_keywords: 
  - "настройка начальной страницы [Visual Studio]"
  - "начальная страница [Visual Studio]"
  - "начальная страница Visual Studio"
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 45
caps.handback.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Настройка начальной страницы в Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Существует несколько способов настройки начальной страницы Visual Studio: например, для этого можно использовать диалоговое окно **Открытие проекта** или открыть решение, загруженное последним.  Также можно отобразить настраиваемую начальную страницу, т. е. страницу XAML Windows Presentation Foundation \(WPF\), которая открывается в окне инструментов и может использоваться для выполнения внутренних команд Visual Studio.  
  
## Настройка начальной страницы по умолчанию  
  
1.  В строке меню выберите **Сервис**, **Параметры**.  
  
2.  Разверните меню **Среда** и выберите **Запуск**.  
  
3.  В списке **При запуске** выберите элемент, который требуется настроить.  
  
## Отображение настраиваемой начальной страницы  
  
1.  Установите настраиваемую начальную страницу одним из следующих способов:  
  
    -   Установите данную страницу из [коллекции Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), с другого веб\-сайта или со страницы своей локальной интрасети.  
  
        > [!NOTE]
        >  Если вы предпочитаете страницу, предназначенную для более ранней версии Visual Studio, то можете обновить ее при помощи пакета SDK для Visual Studio.  См. раздел [Практическое руководство. Обновление настраиваемой начальной страницы Visual Studio](../Topic/How%20to:%20Upgrade%20a%20Visual%20Studio%20Custom%20Start%20Page.md).  
  
         Откройте файл VSIX, содержащий настраиваемую начальную страницу, или скопируйте и вставьте файлы начальной страницы в папку %USERPROFILE% \\Мои документы\\Visual Studio 2015\\StartPages на компьютере.  
  
    -   Создайте собственную начальную страницу, если на вашем компьютере установлен пакет SDK для Visual Studio.  
  
         См. раздел [Создание собственной начальной страницы](../misc/creating-your-own-start-page.md).  
  
2.  В строке меню выберите **Сервис**, **Параметры**.  
  
3.  Разверните меню **Среда** и выберите **Запуск**.  
  
4.  В списке **Настроить начальную страницу** выберите нужную страницу.  
  
> [!NOTE]
>  Если ошибка в настраиваемой начальной странице вызывает сбой Visual Studio, можно запустить Visual Studio в безопасном режиме, а затем настроить использование начальной страницы по умолчанию.  См. раздел [\/SafeMode](../ide/reference/safemode-devenv-exe.md).  
  
## См. также  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Создание собственной начальной страницы](../misc/creating-your-own-start-page.md)