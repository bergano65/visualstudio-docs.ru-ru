---
title: 'Практическое: Создание локализованного пакета загрузчика | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
ms.openlocfilehash: 1083633410c42c63f8c3e9a2ff341a2278f0b63a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153219"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Практическое: Создание локализованного пакета загрузчика
После создания пакета загрузчика, можно создать локализованные версии пакета начального загрузчика, создав два или несколько файлов для каждого языкового стандарта: файл условий лицензии на программное обеспечение (например, *eula.rtf*) и манифест пакета (*package.xml*).  
  
 По умолчанию в Visual Studio 2010 локализованные пакеты начальной загрузки включены только для .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 и F# Runtime 4.0. Чтобы создать локализованные пакеты для других начальных загрузчиков, сделайте следующее.  
  
1.  Создайте папку с именем после имени языкового стандарта в *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >*.  
  
2.  Создайте файл, содержащий условия лицензионного соглашения на использование программного обеспечения, для пакета начального загрузчика и сохраните его в новую папку.  
  
3.  Создание манифеста пакета с именем *package.xml*, обновите строки и язык и региональные параметры и поместить его в новую папку. Если вы уже создали начальный загрузчик для Visual Studio на целевом языке, можно скопировать в Visual Studio *package.xml* файл и измените его на этом шаге.  
  
> [!NOTE]
>  Если вы используете проект установки для развертывания приложений, приложение можно локализовать, изменив **локализации** свойство.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Создание пакета локализованного начального загрузчика  
  
1.  Создайте папку с именем, соответствующим языковому стандарту.  
  
     На 32-разрядных компьютерах, создайте в папке *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  папки.  
  
     На 64-разрядных компьютерах, создайте в папке *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  папки.  
  
     В следующей таблице показано, какие имена папок можно использовать для соотнесения с языковым стандартом.  
  
    |Языковой стандарт|Имя папки|  
    |------------|-----------------|  
    |Китайский (упрощенный)|zh-Hans|  
    |Китайский (традиционный)|zh-Hant|  
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
  
3.  Создание манифеста пакета с именем *package.xml* и поместить его в новую папку. Дополнительные сведения см. в разделе [как: создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Обновите раздел `<Strings>` манифеста пакета, так чтобы язык строк соответствовал языковому стандарту.  
  
5.  Измените значение `<String Name="Culture">` таким образом, чтобы оно соответствовало имени папки.  
  
6.  Сохранить *package.xml* файл.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Создание пакета начального загрузчика для .NET Framework 3.5 Service Pack 1 с локализацией на французском языке  
  
1.  Создайте папку с именем *fr*. Имя папки должно совпадать с именем языкового стандарта.  
  
     На 32-разрядных компьютерах, создайте в папке *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  папки.  
  
     На 64-разрядных компьютерах, создайте в папке *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  папки.  
  
2.  Размещение локализованной версии условий лицензионного соглашения программного обеспечения в *fr* папки.  
  
3.  Копировать *\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml файлы (x86) \Program* файл *fr* папку и откройте файл в конструкторе XML.  
  
4.  Обновите раздел `<Strings>` манифеста пакета, так чтобы строки с сообщениями об ошибках были на французском языке.  
  
5.  Изменение `<String Name="Culture">` значение *fr*.  
  
6.  Сохранить *package.xml* файл.  
  
## <a name="see-also"></a>См. также  
 [Создание пакетов загрузчика](../deployment/creating-bootstrapper-packages.md)   
 [Предварительные условия для развертывания приложения](../deployment/application-deployment-prerequisites.md)   
 [Практическое руководство. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md)