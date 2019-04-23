---
title: Практическое руководство. Создание локализованного пакета загрузчика | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71fbafb46db563c56bafb926b66b88bc39fda2ed
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039355"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Практическое руководство. Создание локализованного пакета загрузчика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Закончив создание пакета начального загрузчика, вы можете сформировать его локализованные версии, создав по два или несколько файлов для каждого языкового стандарта: файл условий лицензионного соглашения на использование программного обеспечения (например, eula.rtf) и манифест пакета (package.xml).  
  
 По умолчанию в Visual Studio 2010 локализованные пакеты начальной загрузки включены только для .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 и F# Runtime 4.0. Чтобы создать локализованные пакеты для других начальных загрузчиков, сделайте следующее.  
  
1. Создайте папку с именем после имени языкового стандарта в \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*.  
  
2. Создайте файл, содержащий условия лицензионного соглашения на использование программного обеспечения, для пакета начального загрузчика и сохраните его в новую папку.  
  
3. Создайте манифест пакета с именем package.xml, обновите строки и культуру и сохраните файл в новую папку. Если вы уже создали начальный загрузчик для Visual Studio с целевым зыком, на этом этапе можно просто скопировать файл Visual Studio package.xml и внести в него необходимые изменения.  
  
> [!NOTE]
>  Если для развертывания приложений используется проект установки, приложение можно локализовать, изменив свойство **Локализация**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Создание пакета локализованного начального загрузчика  
  
1. Создайте папку с именем, соответствующим языковому стандарту.  
  
     На 32-разрядных компьютерах, создайте папку в \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*\ папки.  
  
     На 64-разрядных компьютерах, создайте папку в \Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*\ папки.  
  
     В следующей таблице показано, какие имена папок можно использовать для соотнесения с языковым стандартом.  
  
    |Языковой стандарт|Имя папки|  
    |------------|-----------------|  
    |Китайский (упрощенное письмо)|zh-Hans|  
    |Китайский (традиционное письмо)|zh-Hant|  
    |Чешский|cs|  
    |Немецкий|de|  
    |Английский|en|  
    |Испанский|es|  
    |Французский|fr|  
    |Итальянский|it|  
    |Корейский|ko|  
    |Японский|ja|  
    |Польский|pl|  
    |Португальский (Бразилия)|pt-BR|  
    |Русский|ru|  
    |Турецкий|tr|  
  
2. Создайте файл, содержащий условия лицензионного соглашения на использование программного обеспечения, для пакета начального загрузчика и сохраните его в новую папку.  
  
3. Создайте манифест пакета с именем package.xml и сохраните его в новую папку. Дополнительные сведения см. в разделе [Как Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md).  
  
4. Обновите раздел `<Strings>` манифеста пакета, так чтобы язык строк соответствовал языковому стандарту.  
  
5. Измените значение `<String Name="Culture">` таким образом, чтобы оно соответствовало имени папки.  
  
6. Сохраните файл package.xml.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Создание пакета начального загрузчика для .NET Framework 3.5 Service Pack 1 с локализацией на французском языке  
  
1. Создайте папку с именем fr. Имя папки должно совпадать с именем языкового стандарта.  
  
     На 32-разрядных компьютерах эту папку необходимо создать в директории \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\.  
  
     На 64-разрядных компьютерах — в директории \Program Files (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\.  
  
2. Сохраните локализованную версию условий лицензионного соглашения на использование программного обеспечения в папку с именем fr.  
  
3. Скопируйте файл \Program Files (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml в папку с именем fr и откройте его в программе XML Designer.  
  
4. Обновите раздел `<Strings>` манифеста пакета, так чтобы строки с сообщениями об ошибках были на французском языке.  
  
5. Измените значение `<String Name="Culture">` на fr.  
  
6. Сохраните файл package.xml.  
  
## <a name="see-also"></a>См. также  
 [Создание пакетов загрузчика](../deployment/creating-bootstrapper-packages.md)   
 [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)   
 [Практическое руководство. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md)
