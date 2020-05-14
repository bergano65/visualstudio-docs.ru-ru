---
title: Создание пакетов начального загрузчика
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f84f91ebedd47df8c0804adee35dcbec18d8551
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301011"
---
# <a name="create-bootstrapper-packages"></a>Создание пакетов начального загрузчика
Программа установки — это общий установщик, который можно настроить на обнаружение и установку распространяемых компонентов, таких как файлы установщика Windows (*.MSI*) и исполняемые программы. Установщик также называется начальным загрузчиком. Он программируется с помощью набора XML манифестов, определяющих метаданные для управления установкой компонента.  Каждый перераспределителистный компонент, или предпосылки, который появляется в поле диалога **Prerequisites** для ClickOnce является пакетом загрузчика. Пакет начальной загрузки — это группа директорий и файлов, в которых содержатся файлы манифеста, описывающие порядок установки необходимого компонента.

Сначала начальный загрузчик проверяет, установлены ли необходимые компоненты. Если нет, то начальный загрузчик показывает лицензионные соглашения. Как только конечный пользователь примет условия лицензионного соглашения, начнется установка необходимых компонентов. Если все необходимые компоненты обнаружены, начальный загрузчик просто запустит установщик приложения.

## <a name="create-custom-bootstrapper-packages"></a>Создание пользовательских пакетов загрузчика
Вы можете создать загрузчик манифесты с помощью XML редактор в Visual Studio. Чтобы увидеть пример создания пакета bootstrapper, [см.](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)

Чтобы создать пакет bootstrapper, вы должны создать манифест продукта и, для каждой локализованной версии компонента, манифест пакета также.

* Манифест продукта, *product.xml,* содержит любые нейтральные в отношении языка метаданные для упаковки. Здесь находятся общие метаданные для всех локализованных версий распространяемого компонента.  Чтобы создать этот файл, см. [Как: Создать манифест продукта](../deployment/how-to-create-a-product-manifest.md).

* Манифест пакета, *package.xml,* содержит метаданные, специфичные для языка; обычно он содержит локализованные сообщения об ошибках. Компонент должен содержать хотя бы один манифест пакета для каждой локализованной версии. Чтобы создать этот файл, [см. Как: Создать манифест пакета](../deployment/how-to-create-a-package-manifest.md).

После создания этих файлов необходимо сохранить манифест продукта в папку с именем стандартного начального загрузчика. Файл манифеста пакета следует переместить в папку с именем языкового стандарта. Например, если манифест пакета создан для распространения на английском языке, то файл необходимо положить в папку с названием "en". Повторите эту процедуру для каждого языкового стандарта, например "ja" для японского языка и "de" для немецкого. Окончательный пользовательский пакет начального загрузчика может иметь следующую структуру папок.

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

Затем скопируйте перераспределители файлы в расположение папки загрузчика. Дополнительные сведения см. в разделе [Практическое руководство. Создание локализованного пакета начального загрузчика](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

или, для старых версий Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

или диспетчер конфигурации служб

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

Вы также можете найти расположение флакона загрузчика из значения **Путь** в следующем ключе реестра:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

Для 64-разрядных операционных систем необходимо использовать следующий раздел реестра:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Каждый распространяемый компонент создается в своей подпапке в каталоге пакетов. Манифест продукта и перераспределительных файлов должны быть помещены в этот subfolder. Локализованные версии компонента и пакетные манифесты должны быть помещены в субфандеры, названные в соответствии с названием Culture.

После того как файлы будут скопированы в папку начального загрузчика, пакет начального загрузчика автоматически появится в диалоговом окне **необходимых компонентов** Visual Studio. Если пользовательский пакет начального загрузчика не появился, закройте и снова откройте диалоговое окно **необходимых компонентов**. Для получения дополнительной [информации см.](../ide/reference/prerequisites-dialog-box.md)

В следующей таблице перечислены свойства, которые заполняются начальным загрузчиком автоматически.

|Свойство|Описание|
|--------------|-----------------|
|ApplicationName|Имя приложения.|
|ProcessorArchitecture|Процессор и количество бит на слово в платформе, для которой предназначен исполняемый файл. В эти значения входят:<br /><br /> — Intel<br />— IA64<br />— AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Номер версии для операционных систем Microsoft Windows 95, Windows 98 и Windows ME. Синтаксис версии — Major.Minor.ServicePack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Номер версии для операционных систем Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 и Windows 7. Синтаксис версии — Major.Minor.ServicePack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Версия сборки установки Windows (msi.dll) для выполнения во время установки.|
|[АдминУс](/windows/desktop/Msi/adminuser)|Данное свойство устанавливается, если пользователь имеет права администратора. Значения — true или false.|
|InstallMode|Режим установки показывает, откуда должен быть установлен компонент. В эти значения входят:<br /><br /> — HomeSite: необходимые компоненты должны устанавливаться с веб-сайта поставщика.<br />— SpecificSite: необходимые компоненты должны устанавливаться из выбранного расположения.<br />— SameSite: необходимые компоненты должны устанавливаться из расположения приложения.|

## <a name="separate-redistributables-from-application-installations"></a>Отдельные перераспределители от установок приложений
Размещение распространяемых файлов в проектах установки можно предотвратить. Для этого необходимо создать список распространяемых компонентов в папке RedistList каталога .NET Framework:

`%ProgramFiles%\Microsoft.NET\RedistList`

Перераспределителист — это файл XML, который следует назвать следующим форматом: * \<Название компании>.\< Название компонента>. RedistList.xml*. Например, если компонент называется DataWidgets и разработан компанией Acme, файл необходимо назвать *Acme.DataWidgets.RedistList.xml*. Пример содержания списка распространяемых компонентов:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>См. также раздел
- [Как: Установка предварительных условий с помощью приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Диалоговое окно "Необходимые компоненты"](../ide/reference/prerequisites-dialog-box.md)
- [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)
- [Использование загрузчика Visual Studio 2005 для запуска установки](https://msdn.microsoft.com/magazine/cc163899.aspx)
