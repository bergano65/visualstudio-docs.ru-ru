---
title: "Настройка начальной страницы в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
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
caps.latest.revision: 45
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d797017eb46f38a81f4d5ba6f1999457aa816d1c
ms.openlocfilehash: 69cc33533afd449e50bfc3ecbc8384359253fabb
ms.lasthandoff: 02/22/2017

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
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   

