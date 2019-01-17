---
title: Как выполнить Создание локализованного пакета загрузчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 129f684c7dca4fc8da27286d51a9c3309ed87531
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990403"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Как выполнить Создание пакета локализованного начального загрузчика
Закончив создание пакета начального загрузчика, вы можете сформировать его локализованные версии, создав по два или несколько файлов для каждого языкового стандарта: файл условий лицензионного соглашения на использование программного обеспечения (например, *eula.rtf*) и манифест пакета (*package.xml*).  
  
 По умолчанию в Visual Studio 2010 локализованные пакеты начальной загрузки включены только для .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 и F# Runtime 4.0. Чтобы создать локализованные пакеты для других начальных загрузчиков, сделайте следующее.  
  
1.  Создайте папку с именем после имени языкового стандарта в *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >*.  
  
2.  Создайте файл, содержащий условия лицензионного соглашения на использование программного обеспечения, для пакета начального загрузчика и сохраните его в новую папку.  
  
3.  Создайте манифест пакета с именем *package.xml*, обновите строки и культуру и сохраните файл в новую папку. Если вы уже создали начальный загрузчик для Visual Studio с целевым языком, на этом этапе можно просто скопировать файл Visual Studio *package.xml* и внести в него необходимые изменения.  
  
> [!NOTE]
>  Если для развертывания приложений используется проект установки, приложение можно локализовать, изменив свойство **Локализация**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Создание пакета локализованного начального загрузчика  
  
1.  Создайте папку с именем, соответствующим языковому стандарту.  
  
     На 32-разрядных компьютерах, создайте в папке *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  папки.  
  
     На 64-разрядных компьютерах, создайте в папке *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  папки.  
  
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
  
2.  Создайте файл, содержащий условия лицензионного соглашения на использование программного обеспечения, для пакета начального загрузчика и сохраните его в новую папку.  
  
3.  Создайте манифест пакета с именем *package.xml* и сохраните его в новую папку. Дополнительные сведения см. в разделе [Как создать манифест пакета](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Обновите раздел `<Strings>` манифеста пакета, так чтобы язык строк соответствовал языковому стандарту.  
  
5.  Измените значение `<String Name="Culture">` таким образом, чтобы оно соответствовало имени папки.  
  
6.  Сохраните файл *package.xml*.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Создание пакета начального загрузчика для .NET Framework 3.5 Service Pack 1 с локализацией на французском языке  
  
1.  Создайте папку с именем *fr*. Имя папки должно совпадать с именем языкового стандарта.  
  
     На 32-разрядных компьютерах эту папку необходимо создать в папке *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*.  
  
     На 64-разрядных компьютерах — в папке *\Program Files (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*.  
  
2.  Сохраните локализованную версию условий лицензионного соглашения на использование программного обеспечения в папку с именем *fr*.  
  
3.  Скопируйте файл *\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* в папку с именем *fr* и откройте его в программе XML Designer.  
  
4.  Обновите раздел `<Strings>` манифеста пакета, так чтобы строки с сообщениями об ошибках были на французском языке.  
  
5.  Измените значение `<String Name="Culture">` на *fr*.  
  
6.  Сохраните файл *package.xml*.  
  
## <a name="see-also"></a>См. также  
 [Создание пакетов начального загрузчика](../deployment/creating-bootstrapper-packages.md)   
 [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)   
 [Практическое руководство. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md)