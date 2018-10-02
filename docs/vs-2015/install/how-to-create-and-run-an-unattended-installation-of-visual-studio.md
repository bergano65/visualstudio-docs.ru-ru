---
title: 'Практическое: Создание и выполнение автоматической установки Visual Studio | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 3604c43dc3a406c303b3b056fe3b155efe182e77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570263"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>How to: Create and Run an Unattended Installation of Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Приложение установки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно запустить в режиме автоматической установки (т. е. настроенной тихой установки) через интрасеть вместо выполнения установки с носителя, например DVD-диска. В этом разделе описывается Подготовка [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для этого типа установки из общей сетевой папки.  
  
## <a name="creating-a-network-image"></a>Создание сетевого образа  
 Создайте сетевой образ носителя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-network-image"></a>Создание сетевого образа  
  
1.  Создайте папку на сервере (например, *диска*: \IDEinstall\\).  
  
2.  Скачать установщик [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), а затем запустите *продукта*.exe/Layout *диска*: \IDEinstall\  
  
3.  Общий доступ к папке IDEinstall и установите соответствующие параметры безопасности.  
  
     Сетевой путь приложения установки для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] напоминает \\ \\ *ServerName*\IDEinstall\\*продукта*.exe.  
  
    > [!NOTE]
    >  Установка может завершиться сбоем, если сочетание имени файла и пути превышает максимально допустимое число знаков (260). Максимальная длина пути в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] — 221 символ.  Максимальная длина локального пути — 70 символов; сетевого пути — 39 символов.  
  
     Установка может завершиться сбоем, если имена папок в пути включают пробелы (например, "\\\\*ServerName*\IDE install» или \\ \\ *ServerName*\Visual studio\\).  
  
## <a name="deploying-visual-studio-in-unattended-mode"></a>Развертывание Visual Studio в автоматическом режиме  
 Для развертывания [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в автоматическом режиме необходимо изменить файл AdminDeployment.xml. Чтобы сделать это, необходимо сначала создать файл AdminDeployment.xml с помощью `/CreateAdminFile`  *\<расположение файла >* параметра командной строки. Затем этот файл можно использовать для переноса развертывания Visual Studio в сеть либо для ввода в среду установки в случае его размещения в каталоге *диск*:\IDEinstall\packages. Файл AdminDeployment.xml не является уникальным для операционной системы, архитектуры, выпуска Visual Studio или языка операционной системы.  
  
> [!CAUTION]
>  Иногда элементы, перечисленные как выбранные в файле AdminDeployment.xml, не устанавливаются. Чтобы решить эту проблему, поместите элементы с пометкой "Selected="yes"" в **конец** файла AdminDeployment.xml.  
>   
>  Если вы не хотите устанавливать необязательные зависимости элемента, сначала нужно выбрать родительский элемент, а затем отменить выбор необязательных зависимостей после него, как показано на снимке экрана ниже.  
>   
>  ![Элементы установки в конце файла AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")  
>   
>  Еще один способ — просто пропустить необязательный дочерний элемент. Иными словами, не включайте элементы с пометкой "Selected="no"". Однако все элементы с пометкой "Selected="yes"" необходимо по-прежнему поместить в конце файла AdminDeployment.xml.  
  
> [!IMPORTANT]
>  Во время установки компьютер может автоматически перезагружаться один или несколько раз. После перезапуска необходимо снова войти в систему с той же учетной записью пользователя, с которой вы входили для выполнения установки до перезагрузки компьютера. Автоматических перезагрузок можно избежать, если предварительно установить необходимые компоненты до запуска автоматической установки. Дополнительные сведения см. в подразделе под названием «Установка без перезапуска» в [руководства администратора Visual Studio](../install/visual-studio-administrator-guide.md).  
  
 Схема файла AdminDeployment содержит следующие элементы:  
  
|Элемент|Атрибут|Значения|Описание|  
|-------------|---------------|------------|-----------------|  
|BundleCustomizations|TargetDir|*Путь*|Поведение аналогично переопределению пути в интерфейсе пользователя приложения установки. Этот элемент пропускается, если Visual Studio уже установлена.|  
|BundleCustomizations|NoWeb|Да&#124;по умолчанию|Если значение этого элемента — yes (да), приложение установки не будет пытаться выйти в Интернет во время установки.|  
|SelectableItemCustomization|Hidden|Да&#124;нет|Если значение этого элемента — yes (да), элемент Selectable в дереве настройки скрывается.|  
|SelectableItemCustomization|Selected|Да&#124;нет|Выбирает или отменяет выделение выделяемого элемента в дереве пользовательской настройки.|  
|BundleCustomizations|Feed|Путь|Расположение веб-канала, который хочет применять пользователь.  Этот веб-канал используется для последующих операций изменения на компьютере (по умолчанию Default).|  
|BundleCustomizations|SuppressRefreshPrompt|Да&#124;по умолчанию|Пользователю не выводится запрос на обновление установки, если доступна более новая версия.|  
|BundleCustomizations|NoRefresh|Да&#124;по умолчанию|При наличии более новой версии установка не обновляется.|  
|BundleCustomizations|NoCacheOnlyMode|Да&#124;по умолчанию|Предотвращает предварительное заполнение кэша пакета.|  
  
> [!WARNING]
>  Приложение установки будет следовать указанному состоянию SelectableItem, даже если он скрыт. Например, если необходимо всегда устанавливать выбираемый элемент, можно пометить его как скрытый и выбранный.  
  
#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Создание автоматической установки Visual Studio  
  
1.  В файле *диск*:\IDEinstall\AdminDeployment.xml измените значение атрибута NoWeb элемента BundleCustomizations с "default" на "yes", как показано в следующем примере:  
  
     Измените `<BundleCustomizations TargetDir="default" NoWeb="default"/>` на `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`  
  
2.  Измените требуемым образом атрибут SelectableItemCustomization для дополнительных компонентов, а затем сохраните файл.  
  
## <a name="running-unattended-setup"></a>Выполнение автоматической установки  
 Автоматическую установку можно запустить, автоматически запустив приложение установки Visual Studio на клиентских компьютерах или разрешив пользователям запустить это приложение самостоятельно, используя заданные вами параметры.  
  
#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Автоматическая установка на клиентском компьютере  
  
-   Откройте **запустить** меню, выберите **запуска**и введите \\ \\ *ServerName*\IDEinstall\vs_*продукта*.exe/adminfile *PathOfTheAdmindeployment.xmlFile**AdditionalParametersAsNeeded*  
  
     Например, можно указать следующую командную строку: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Разрешение клиентам вручную устанавливать Visual Studio с предопределенными параметрами  
  
1.  Скопируйте настроенный файл AdminDeployment.xml в сетевую папку, доступную только для чтения (например, \\ \\ *ServerName*\IDEinstall\packages\AdminDeployment.xml).  
  
2.  Разрешите пользователям выполнять установку из этой общей папки.  
  
## <a name="maintaining-an-installation"></a>Обслуживание установки  
 Если открыть **Панель управления** и снова запустить приложение установки, можно изменить компоненты Visual Studio, удалить языки программирования, а также восстановить или удалить Visual Studio.  
  
> [!NOTE]
>  Для запуска программы установки в режиме обслуживания пользователь должен обладать полномочиями администратора на локальном компьютере.  
  
#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Обслуживание установки на клиентском компьютере  
  
-   Откройте **Панель управления**и выберите **Программы и компоненты**.  
  
-   Выберите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], а затем выберите **изменение**.  
  
#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Изменение параметров AdminDeployment на клиентском компьютере после установки Visual Studio  
  
1.  Обновите файл AdminDeployment.xml по мере необходимости.  
  
2.  Нажмите кнопку **Пуск** и выберите **Выполнить**.  
  
3.  Введите следующий текст: \\ \\ *ServerName*\IDEinstall\vs_*продукта*.exe/adminfile PathToAdmindeployment.xml файла  
  
     ДополнительныеПараметрыПоМереНеобходимости  
  
     Например, можно указать следующую командную строку: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
 Восстановление является параметром по умолчанию после установки Visual Studio. Если восстановить Visual Studio с помощью обновленного/adminfile, будут переопределены текущие параметры развертывания администратора теми значениями, которые вызывает обновленный файл AdminDeployment.xml.  
  
## <a name="updating-an-installation"></a>Обновление установки  
 Корпорация Microsoft выпустила несколько обновлений для Visual Studio 2015. В этом разделе объясняется, как обновить ваш образ для автоматической установки Visual Studio 2015, чтобы он включает в себя обновления.  
  
#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Чтобы обновить автоматической установки Visual Studio  
  
1.  Найдите файл Product.exe в существующий образ сети, щелкните его правой кнопкой мыши и нажмите кнопку **свойства**.  
  
2.  Нажмите кнопку **сведения** вкладке, а затем запишите **версия_продукта** свойство.  
  
     ![Пример диалогового окна свойств в рамках автоматической установки Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "автоматической установки - диалоговое окно «Свойства»")  
  
3.  ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Если версия продукта 14.0.24720.0 или 14.0.24720.1, выполните следующие действия.  
4.  1.  Запустите *Product.exe* /Layout *диска:* \IDEinstall на компьютере с доступом к Интернету. (Например, выполните: `vs_enterprise.exe /Layout d:\IDEinstall`.)  
  
    2.  После завершения / Layout, скопируйте новый образ в новое расположение.  
  
    3.  Создать и изменить файл AdminDeployment.xml. Чтобы сделать это, используйте `/CreateAdminFile`  *\<расположение файла >* параметра командной строки. (Дополнительные сведения см. в разделе «Развертывание Visual Studio в автоматическом режиме» данной статьи.)  
  
    4.  На клиентском компьютере выполните следующую команду, чтобы обновить экземпляр Visual Studio, который был установлен ранее: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe*  /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart».  
  
         Например выполните: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`  
5.  ###### <a name="for-other-product-version-values-follow-these-steps"></a>Для других значений версии продукта выполните следующие действия.  
6.  1.  Запустите *Product.exe* /Layout *диска:* \IDEinstall на компьютере с доступом к Интернету. (Например, выполнить `vs-enterprise.exe /Layout d:\IDEinstall`.)  
  
    2.  После завершения / Layout, скопируйте новый образ в новое расположение. (Или вместо этого можно переопределить существующий образ сети).  
  
    3.  Создание и изменение его файла AdminDeployment.xml. Чтобы сделать это, используйте `/CreateAdminFile`  *\<расположение файла >* параметра командной строки. (Дополнительные сведения см. в разделе «Развертывание Visual Studio в автоматическом режиме» данной статьи.)  
  
    4.  Если скопировать изображение в новое расположение, необходимо запустить следующую команду на клиентском компьютере для обновления копии Visual Studio, который был установлен ранее: "\\\\*server1*\IDEinstall_Updated_1\\ *Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart».  
  
         Например выполните: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`  
  
    5.  Если переопределить существующий образ сети, можно выполнить команду, как показано на предыдущем шаге, или можно сделать следующее:  
  
    6.  1.  Откройте **Панель управления**и выберите **Программы и компоненты**.  
  
        2.  Выберите **Visual Studio**, а затем выберите **изменение**.  
  
        3.  После запуска Visual Studio в режиме обслуживания выберите **изменить**.  
  
        4.  Последнее обновление должно отображаться на странице компонентов. Другие функции, которые вы хотите установить, нажмите кнопку **Далее**, а затем нажмите кнопку **обновление** для установки обновления и новые функции.  
  
## <a name="registering-the-product"></a>Регистрация продукта  
 После завершения установки вы можете зарегистрировать свою копию [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прямо из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-register"></a>Регистрация  
  
1.  В меню **Справка** выберите **Зарегистрировать продукт**.  
  
2.  Введите ключ продукта.  
  
     (Дополнительные сведения см. в разделе [как: найти ключ продукта Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) и [как: автоматическое применение ключей продуктов при развертывании Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) разделы.)  
  
## <a name="see-also"></a>См. также  
 [Установка Visual Studio](../install/install-visual-studio-2015.md)