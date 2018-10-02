---
title: Создание пакетов загрузчика | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee6badf48d0d196001c948495f9b658114c66ff6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563564"
---
# <a name="creating-bootstrapper-packages"></a>Создание пакетов загрузчика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [создание пакетов загрузчика](https://docs.microsoft.com/visualstudio/deployment/creating-bootstrapper-packages).  
  
Программа установки — это общий установщик, который можно настроить на обнаружение и установку распространяемых компонентов, таких как файлы установщика Windows (.MSI) и исполняемые программы. Установщик также называется начальным загрузчиком. Он программируется с помощью набора XML манифестов, определяющих метаданные для управления установкой компонента.  
  
 Сначала начальный загрузчик проверяет, установлены ли необходимые компоненты. Если нет, то начальный загрузчик показывает лицензионные соглашения. Как только конечный пользователь примет условия лицензионного соглашения, начнется установка необходимых компонентов. Если все необходимые компоненты обнаружены, начальный загрузчик просто запустит установщик приложения.  
  
## <a name="creating-custom-packages"></a>Создание пользовательских пакетов  
 Для создания манифестов можно использовать редактор XML в Visual Studio. Дополнительные сведения см. в разделах [How to: Create a Package Manifest](../deployment/how-to-create-a-package-manifest.md) и [How to: Create a Product Manifest](../deployment/how-to-create-a-product-manifest.md). Пример создания пакета загрузчика см. в разделе [Пошаговое руководство. Создание пользовательского загрузчика для вывода окна с предупреждением о конфиденциальности](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Чтобы создать пакет начального загрузчика, необходимо отправить распространяемый компонент в форме EXE- или MSI-файла в Генератор манифестов начального загрузчика. После этого Генератор манифестов начального загрузчика создаст следующие файлы.  
  
-   Манифест продукта (product.xml), содержащий метаданные для пакета, не зависящие от языка. Здесь находятся общие метаданные для всех локализованных версий распространяемого компонента.  
  
-   Манифест пакета (package.xml), содержащий метаданные, которые относятся к конкретному языку. Обычно они содержат локализованные сообщения об ошибках. Компонент должен содержать хотя бы один манифест пакета для каждой локализованной версии.  
  
 После создания этих файлов необходимо сохранить манифест продукта в папку с именем стандартного начального загрузчика. Файл манифеста пакета следует переместить в папку с именем языкового стандарта. Например, если манифест пакета создан для распространения на английском языке, то файл необходимо положить в папку с названием "en". Повторите эту процедуру для каждого языкового стандарта, например "ja" для японского языка и "de" для немецкого. Окончательный пользовательский пакет начального загрузчика может иметь следующую структуру папок.  
  
 `CustomBootstrapperPackage`  
  
 `product.xml`  
  
 `CustomBootstrapper.msi`  
  
 `de`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `en`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `ja`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 Скопируйте распространяемые файлы в папку начального загрузчика. Для получения дополнительной информации см. [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 или  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Определить расположение папки начального загрузчика можно по значению **Путь** в следующем разделе реестра:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 Для 64-разрядных операционных систем необходимо использовать следующий раздел реестра:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Каждый распространяемый компонент создается в своей подпапке в каталоге пакетов. Манифест продукта и распространяемые файлы сохраняются в эту подпапку. Локализованные версии манифестов компонента и пакета помещаются в подпапки с именем, соответствующим названию культуры.  
  
 После того как файлы будут скопированы в папку начального загрузчика, пакет начального загрузчика автоматически появится в диалоговом окне необходимых компонентов Visual Studio. Если пользовательский пакет начального загрузчика не появился, закройте и снова откройте диалоговое окно необходимых компонентов. Дополнительные сведения см. в разделе [Диалоговое окно «Необходимые компоненты»](../ide/reference/prerequisites-dialog-box.md).  
  
 В следующей таблице перечислены свойства, которые заполняются начальным загрузчиком автоматически.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|ApplicationName|Имя приложения.|  
|ProcessorArchitecture|Процессор и количество бит на слово в платформе, для которой предназначен исполняемый файл. В эти значения входят:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Номер версии для операционных систем Microsoft Windows 95, Windows 98 и Windows ME. Синтаксис версии — Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/library/aa372495\(v=vs.140\).xaspx)|Номер версии для операционных систем Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 и Windows 7. Синтаксис версии — Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|Версия сборки установщика Windows (msi.dll), который запускается во время установки.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Данное свойство устанавливается, если пользователь имеет права администратора. Значения — true или false.|  
|InstallMode|Режим установки показывает, откуда должен быть установлен компонент. В эти значения входят:<br /><br /> -HomeSite: необходимые компоненты устанавливаются с веб-сайта поставщика.<br />-SpecificSite: необходимые компоненты устанавливаются из выбранного расположения.<br />-SameSite: необходимые компоненты устанавливаются в том же расположении, что и приложение.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Отделение распространяемых компонентов от установок приложения  
 Размещение распространяемых файлов в проектах установки можно предотвратить. Для этого необходимо создать список распространяемых компонентов в папке RedistList каталога .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Список распространяемых компонентов — это XML-файл, которому необходимо присвоить имя в следующем формате: *Название компании*.*Название компонента*.RedistList.xml. Например, если компонент называется Datawidgets и разработан компанией Acme, файл необходимо назвать Acme.DataWidgets.RedistList.xml. Пример содержания списка распространяемых компонентов:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Диалоговое окно необходимых компонентов](../ide/reference/prerequisites-dialog-box.md)   
 [Продукт и справочник по схемам пакета](../deployment/product-and-package-schema-reference.md)   
 [Используйте загрузчик Visual Studio 2005 для запуска вашей установки.](http://go.microsoft.com/fwlink/?LinkId=107537)



