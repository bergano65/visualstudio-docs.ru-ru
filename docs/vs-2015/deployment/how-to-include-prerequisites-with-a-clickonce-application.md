---
title: 'Практическое: Включение требуемых компонентов в дистрибутив приложения ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 1a58e305b1214a6b8d710ef08126d241f381a051
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212203"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Практическое руководство. Включение требуемых компонентов в дистрибутив приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Перед распространением программного обеспечения необходимых компонентов с приложением [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] следует загрузить на компьютер разработчика пакеты установщиков этих необходимых компонентов. При публикации приложения и выберите **загрузить необходимые компоненты с местоположения моего приложения**, произойдет ошибка, если пакеты установщиков отсутствуют в **пакетов** папки.  
  
> [!NOTE]
>  Чтобы добавить пакет установщика для .NET Framework, см. в разделе [руководство по развертыванию .NET Framework для разработчиков](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Добавление пакета установщика с помощью файла Package.xml  
  
1.  В проводнике откройте **пакетов** папки.  
  
     Путь по умолчанию: C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 32-разрядной системы) и C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 64-разрядной системы).  
  
2.  Откройте папку необходимого компонента, который вы хотите добавить, а затем откройте папку языка для установленной версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (например, **en** для английского языка).  
  
3.  В блокноте откройте **Package.xml** файл.  
  
4.  Найдите **имя** элемент, содержащий **http://go.microsoft.com/fwlink**и скопируйте URL-адрес. Включить **LinkID** часть.  
  
    > [!NOTE]
    >  Если не **имя** элемент содержит **http://go.microsoft.com/fwlink**откройте **Product.xml** файл в корневой папке необходимого компонента и найдите **fwlink** строка.  
  
    > [!IMPORTANT]
    >  Некоторые необходимые компоненты имеют несколько пакетов установщиков (например, для 32-разрядных или 64-разрядных систем). При наличии нескольких **имя** элементы содержат **fwlink**, оставшиеся шаги необходимо повторить для каждого из них.  
  
5.  Вставьте URL-адрес в адресную строку браузера, а затем, при появлении запроса на выполнение или сохранение нажмите **Сохранить**.  
  
     На этом шаге файл установщика загружается на компьютер.  
  
6.  Скопируйте файл в корневую папку необходимого компонента.  
  
     Например, для необходимого компонента "Установщик Windows 4.5" скопируйте файл в папку \Packages\WindowsInstaller4_5.  
  
     Теперь можно распространить пакет установщика с приложением.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)



