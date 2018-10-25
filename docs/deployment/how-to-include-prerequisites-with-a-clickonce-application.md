---
title: 'Практическое: Включение требуемых компонентов в дистрибутив приложения ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78d28da26cd01b804f8527e42c9ed3aa7977ed10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917860"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Практическое: Включение требуемых компонентов в дистрибутив приложения ClickOnce
Перед распространением программного обеспечения необходимых компонентов с приложением [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] следует загрузить на компьютер разработчика пакеты установщиков этих необходимых компонентов. При публикации приложения и выберите **загрузить необходимые компоненты с местоположения моего приложения**, произойдет ошибка, если пакеты установщиков отсутствуют в **пакетов** папки.  
  
> [!NOTE]
>  Чтобы добавить пакет установщика для .NET Framework, см. в разделе [руководство по развертыванию .NET Framework для разработчиков](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
##  <a name="Package"></a> Добавление пакета установщика с помощью файла Package.xml  
  
1. В проводнике откройте **пакетов** папки.  
  
    По умолчанию это *C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* на 32-разрядной системе и *C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* на 64-разрядной системе.  
  
2. Откройте папку необходимого компонента, который вы хотите добавить, а затем откройте папку языка для установленной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (например, **en** для английского языка).  
  
3. В блокноте откройте *Package.xml* файл.  
  
4. Найдите **имя** элемент, содержащий **http://go.microsoft.com/fwlink**и скопируйте URL-адрес. Включить **LinkID** часть.  
  
   > [!NOTE]
   >  Если не **имя** элемент содержит **http://go.microsoft.com/fwlink**откройте **Product.xml** файл в корневой папке необходимого компонента и найдите **fwlink** строка.  
  
   > [!IMPORTANT]
   >  Некоторые необходимые компоненты имеют несколько пакетов установщиков (например, для 32-разрядных или 64-разрядных систем). При наличии нескольких **имя** элементы содержат **fwlink**, оставшиеся шаги необходимо повторить для каждого из них.  
  
5. Вставьте URL-адрес в адресную строку браузера, а затем, при появлении запроса на выполнение или сохранение нажмите **Сохранить**.  
  
    На этом шаге файл установщика загружается на компьютер.  
  
6. Скопируйте файл в корневую папку необходимого компонента.  
  
    Например, установщик Windows версии 4.5 необходимого компонента, скопируйте файл в *\Packages\WindowsInstaller4_5* папки.  
  
    Теперь можно распространить пакет установщика с приложением.  
  
## <a name="see-also"></a>См. также  
 [Как: установить обязательные компоненты приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)