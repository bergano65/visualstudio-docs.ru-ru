---
title: Практическое руководство. Включить необходимые компоненты ClickOnce-приложения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc9ba407e91ddc8125d2836c8e2bb4329d5ad91f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993875"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Практическое руководство. Включение необходимых компонентов для приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Перед распространением программного обеспечения необходимых компонентов с приложением [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] следует загрузить на компьютер разработчика пакеты установщиков этих необходимых компонентов. При публикации приложения и выберите **загрузить необходимые компоненты с местоположения моего приложения**, произойдет ошибка, если пакеты установщиков отсутствуют в **пакетов** папки.  
  
> [!NOTE]
>  Чтобы добавить пакет установщика для .NET Framework, см. в разделе [руководство по развертыванию .NET Framework для разработчиков](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Добавление пакета установщика с помощью файла Package.xml  
  
1.  В проводнике откройте папку **Packages**.  
  
     Путь по умолчанию: C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 32-разрядной системы) и C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 64-разрядной системы).  
  
2.  Откройте папку необходимого компонента, который требуется добавить, а затем папку языка для установленной версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (например, **ru** для русского языка).  
  
3.  В блокноте откройте файл **Package.xml**.  
  
4.  Найдите **имя** элемент, содержащий **http://go.microsoft.com/fwlink**и скопируйте URL-адрес. Включите часть **LinkID**.  
  
    > [!NOTE]
    >  Если не **имя** элемент содержит **http://go.microsoft.com/fwlink**откройте **Product.xml** файл в корневой папке необходимого компонента и найдите **fwlink** строка.  
  
    > [!IMPORTANT]
    >  Некоторые необходимые компоненты имеют несколько пакетов установщиков (например, для 32-разрядных или 64-разрядных систем). Если строка **fwlink** содержится в нескольких элементах **Имя**, оставшиеся действия следует выполнить для каждого из них.  
  
5.  Вставьте URL-адрес в адресную строку браузера, а затем, при получении запроса на выполнение или сохранение, нажмите кнопку **Сохранить**.  
  
     На этом шаге файл установщика загружается на компьютер.  
  
6.  Скопируйте файл в корневую папку необходимого компонента.  
  
     Например, для необходимого компонента "Установщик Windows 4.5" скопируйте файл в папку \Packages\WindowsInstaller4_5.  
  
     Теперь можно распространить пакет установщика с приложением.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
