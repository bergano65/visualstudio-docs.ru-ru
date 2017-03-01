---
title: "MSI и VSIX развертывание доменного языка | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: beb505dca6f5b52046ca87e854260f4b222079c8
ms.lasthandoff: 02/22/2017

---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Развертывание доменного языка с использование MSI и VSIX
Доменный язык можно установить на локальном компьютере или на других компьютерах. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]должна быть установлена на конечном компьютере.  
  
##  <a name="a-namewhicha-choosing-between-vsix-and-msi-deployment"></a><a name="which"></a>Выбор между VSIX и MSI развертывания  
 Развертывание доменного языка двумя способами.  
  
|Метод|Преимущества|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения)|Очень проста в развертывании: копии и выполнять **.vsix** файл из проекта DslPackage.<br /><br /> Дополнительные сведения см. [Установка и удаление доменного языка с помощью VSX](#Installing).|  
|MSI (файл установщика)|— Позволяет пользователю открыть [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , дважды щелкнув файл DSL.<br />— Связывает значка с типом файла DSL на целевом компьютере.<br />— Связывает XSD (XML schema) с типом файла DSL. Это позволяет избежать предупреждения, когда файл загружается в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Проект установки необходимо добавить в решение для создания файла MSI.<br /><br /> Дополнительные сведения см. в разделе [развертывание DSL с помощью MSI-файл](#msi).|  
  
##  <a name="a-nameinstallinga-installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a>Установка и удаление доменного языка с помощью VSX  
 При установке DSL этим методом, пользователь может открыть файл DSL изнутри [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], но не удается открыть файл из проводника Windows.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Установка с помощью VSX DSL  
  
1.  На компьютере, найдите **.vsix** файл, который был создан проектом пакета DSL.  
  
    1.  В **обозревателе решений**, щелкните правой кнопкой мыши **DslPackage** проекта и нажмите кнопку **открыть папку в проводнике Windows**.  
  
    2.  Locate the file **bin\\\*\\***YourProject***. DslPackage.vsix**  
  
2.  Копировать **.vsix** файл на конечный компьютер, на котором требуется установить DSL. Это может быть как ваш собственный компьютер, так и любой другой.  
  
    -   На конечном компьютере должен быть один из выпусков [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] с поддержкой DSL во время выполнения. Дополнительные сведения см. в разделе [поддерживается выпуска Visual Studio по SDK визуализации моделирования &](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   На конечном компьютере должен быть один из выпусков [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в **DslPackage\source.extensions.manifest**.  
  
3.  На целевом компьютере, дважды щелкните **.vsix** файла.  
  
     Откроется**установщик расширений Visual Studio** , который устанавливает расширение.  
  
4.  Запустите или перезапустите [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Чтобы проверить DSL, используйте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для создания файла с расширением, определенные для DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Удаление доменного языка, установленного с помощью VSX  
  
1.  На **средства** меню, щелкните **Диспетчер расширений**.  
  
2.  Разверните узел **Установленные расширения**.  
  
3.  Выберите модуль, в котором определен DSL, а затем щелкните **удаление**.  
  
 Иногда неисправное расширение не удается загрузить, в результате чего в окне ошибок создается отчет, который не отображается в диспетчере расширений. В этом случае расширение можно удалить, удалив файл из следующей папки:  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="a-namemsia-deploying-a-dsl-in-an-msi"></a><a name="msi"></a>Развертывание DSL в MSI  
 Определив файл MSI (установщик Windows) для DSL, можно разрешить пользователям открывать файлы DSL из проводника Windows. Значок и короткое описание также можно связать с расширением имени файла. Кроме того пакет MSI можно установить XSD, который может использоваться для проверки файлов DSL. Если требуется, можно добавить другие компоненты в MSI-ФАЙЛ, который будет установлен в то же время.  
  
 Дополнительные сведения о MSI-файлы и другие варианты развертывания см. в разделе [развертывание приложений, служб и компонентов](../deployment/deploying-applications-services-and-components.md).  
  
 Для создания файла MSI, добавление проекта установки для вашего [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решения. Самый простой способ создания проекта установки является использование шаблона CreateMsiSetupProject.tt, который можно загрузить с [VMSDK сайта](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Развертывание DSL в MSI  
  
1.  Задать `InstalledByMsi` в манифесте расширения. Это предотвращает VSX устанавливается и удаляется только по MSI-ФАЙЛ. Это важно, если другие компоненты, которые будут включены в MSI-ФАЙЛ.  
  
    1.  Откройте DslPackage\source.extension.tt  
  
    2.  Вставьте следующую строку перед `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Создать или изменить значок, который будет представлять DSL в проводнике Windows. Например, изменить **DslPackage\Resources\File.ico**  
  
3.  Убедитесь, что верны следующие атрибуты DSL:  
  
    -   В обозревателе DSL щелкните корневой узел и в окне свойств просмотрите:  
  
        -   Описание  
  
        -   Версия  
  
    -   Щелкните **редактор** узел и в окне свойств щелкните **значок**. Задайте значение для ссылки на файл значка в **DslPackage\Resources**, такие как **File.ico**  
  
    -   На **построения** откройте в меню **Configuration Manager**и выберите конфигурацию, который вы хотите создать, например **выпуска** или **отладки**.  
  
4.  Последовательно выберите пункты [визуализации и моделирования SDK Домашняя страница](http://go.microsoft.com/fwlink/?LinkID=186128)и от **загрузки** вкладку, загрузите **CreateMsiSetupProject.tt**.  
  
5.  Добавить **CreateMsiSetupProject.tt** в проект Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]создаст файл с именем **CreateMsiSetupProject.vdproj**.  
  
6.  В проводнике Windows, скопируйте Dsl\\*.vdproj в новую папку с именем установки.  
  
     (Если требуется, можно теперь запретить CreateMsiSetupProject.tt проект Dsl.)  
  
7.  В **обозревателе решений**, добавьте **установки\\\*.vdproj** существующего проекта.  
  
8.  На **проекта** меню, щелкните **зависимости проекта**.  
  
     В **зависимости проекта** диалогового окна выберите проект установки.  
  
     Установите флажок рядом с **DslPackage**.  
  
9. Выполните повторную сборку решения.  
  
10. В проводнике Windows найдите построенный MSI-файл в проект установки.  
  
     Скопируйте файл MSI на компьютер, на котором требуется установить DSL. Дважды щелкните файл MSI. Запуск установщика.  
  
11. На целевом компьютере создайте новый файл с расширением доменного языка. Убедитесь, что:  
  
    -   В списке проводника Windows файл имеет значок и описание, которое было определено.  
  
    -   Если дважды щелкнуть файл [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] запускается и открывает файл DSL в редакторе DSL.  
  
 При необходимости можно создать проект установки вручную, вместо текстового шаблона. Пошаговое руководство, которое включает в себя эту процедуру в разделе Глава 5 [визуализации и моделирования SDK лаборатории](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Удаление доменного языка, установленная с помощью установщика Windows  
  
1.  В Windows откройте **программы и компоненты** панели управления.  
  
2.  Удалите DSL.  
  
3.  Перезапустите Visual Studio.
