---
title: Практическое руководство. Создание и запуск автоматической установки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 26e059d4fdc8eadd422924dd6bbda6f7c945ccfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843271"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>How to: Create and Run an Unattended Installation of Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Приложение установки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно запустить в режиме автоматической установки (т. е. настроенной тихой установки) через интрасеть вместо выполнения установки с носителя, например DVD-диска. В этом разделе описано, как подготовить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для этого типа установки из сетевой папки.

## <a name="creating-a-network-image"></a>Создание сетевого образа
 Создайте сетевой образ носителя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-create-a-network-image"></a>Создание сетевого образа

1. Создайте на сервере папку (например, *диск*:\IDEinstall\\).

2. Скачайте установщик на веб-сайте [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), а затем выполните команду *продукт*.exe /Layout *диск*:\IDEinstall\.

3. Предоставьте общий доступ к папке IDEinstall и установите необходимые параметры безопасности.

     Сетевой путь приложения установки для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] имеет следующий вид: \\\\*Serverимя_сервера*\IDEinstall\\*продукт*.exe.

    > [!NOTE]
    > Установка может завершиться сбоем, если сочетание имени файла и пути превышает максимально допустимое число знаков (260). Максимальная длина пути в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] — 221 символ.  Максимальная длина локального пути — 70 символов; сетевого пути — 39 символов.

     Также может произойти сбой установки, если имена папок в пути содержат пробелы (например, " \\ \\ *ServerName*\иде Install" или \\ \\ *ServerName*\висуал Studio \\ ).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Развертывание Visual Studio в автоматическом режиме
 Для развертывания [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в автоматическом режиме необходимо изменить файл AdminDeployment.xml. Для этого необходимо сначала создать файл AdminDeployment.xml с помощью `/CreateAdminFile` *\<file location>* параметра командной строки. Затем этот файл можно использовать для переноса развертывания Visual Studio в сеть либо для ввода в среду установки в случае его размещения в каталоге *диск*:\IDEinstall\packages. Файл AdminDeployment.xml не является уникальным для операционной системы, архитектуры, выпуска Visual Studio или языка операционной системы.

> [!CAUTION]
> Иногда элементы, перечисленные как выбранные в файле AdminDeployment.xml, не устанавливаются. Чтобы решить эту проблему, поместите элементы с пометкой "Selected="yes"" в **конец** файла AdminDeployment.xml.
>
> Если вы не хотите устанавливать необязательные зависимости элемента, сначала нужно выбрать родительский элемент, а затем отменить выбор необязательных зависимостей после него, как показано на снимке экрана ниже.
>
> ![Элементы установки в конце файла AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
> Еще один способ — просто пропустить необязательный дочерний элемент. Иными словами, не включайте элементы с пометкой "Selected="no"". Однако все элементы с пометкой "Selected="yes"" необходимо по-прежнему поместить в конце файла AdminDeployment.xml.

> [!IMPORTANT]
> Во время установки компьютер может автоматически перезагружаться один или несколько раз. После перезапуска необходимо снова войти в систему с той же учетной записью пользователя, с которой вы входили для выполнения установки до перезагрузки компьютера. Автоматических перезагрузок можно избежать, если предварительно установить необходимые компоненты до запуска автоматической установки. Более подробную информацию см. в подразделе под названием "Установка без перезапуска" в разделе [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

 Схема файла AdminDeployment содержит следующие элементы:

|Элемент|Атрибут|Значения|Описание|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Путь*|Поведение аналогично переопределению пути в интерфейсе пользователя приложения установки. Этот элемент пропускается, если Visual Studio уже установлена.|
|BundleCustomizations|NoWeb|да&#124;по умолчанию|Если значение этого элемента — yes (да), приложение установки не будет пытаться выйти в Интернет во время установки.|
|SelectableItemCustomization|Скрытый|даs&#124;нет|Если значение этого элемента — yes (да), элемент Selectable в дереве настройки скрывается.|
|SelectableItemCustomization|Selected|даs&#124;нет|Выбирает или отменяет выделение выделяемого элемента в дереве пользовательской настройки.|
|BundleCustomizations|Веб-канал|Путь|Расположение веб-канала, который хочет применять пользователь.  Этот веб-канал используется для последующих операций изменения на компьютере (по умолчанию Default).|
|BundleCustomizations|SuppressRefreshPrompt|да&#124;по умолчанию|Пользователю не выводится запрос на обновление установки, если доступна более новая версия.|
|BundleCustomizations|NoRefresh|да&#124;по умолчанию|При наличии более новой версии установка не обновляется.|
|BundleCustomizations|NoCacheOnlyMode|да&#124;по умолчанию|Предотвращает предварительное заполнение кэша пакета.|

> [!WARNING]
> Приложение установки будет следовать указанному состоянию SelectableItem, даже если он скрыт. Например, если необходимо всегда устанавливать выбираемый элемент, можно пометить его как скрытый и выбранный.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Создание автоматической установки Visual Studio

1. В файле *диск*:\IDEinstall\AdminDeployment.xml измените значение атрибута NoWeb элемента BundleCustomizations с "default" на "yes", как показано в следующем примере:

     Измените `<BundleCustomizations TargetDir="default" NoWeb="default"/>` на `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`.

2. Измените требуемым образом атрибут SelectableItemCustomization для дополнительных компонентов, а затем сохраните файл.

## <a name="running-unattended-setup"></a>Выполнение автоматической установки
 Автоматическую установку можно запустить, автоматически запустив приложение установки Visual Studio на клиентских компьютерах или разрешив пользователям запустить это приложение самостоятельно, используя заданные вами параметры.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Автоматическая установка на клиентском компьютере

- Откройте меню **Пуск**, выберите **Выполнить** и введите \\\\*имя_сервера*\IDEinstall\vs_*продукт*.exe /adminfile *путь_к_файлу_Admindeployment.xml*<em>дополнительные_параметры</em>

   Например, можно указать следующую командную строку: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Разрешение клиентам вручную устанавливать Visual Studio с предопределенными параметрами

1. Скопируйте настроенный файл AdminDeployment.xml в сетевую общую папку, доступную только для чтения (например, \\\\*ИмяСервера*\IDEinstall\packages\AdminDeployment.xml).

2. Разрешите пользователям выполнять установку из этой общей папки.

## <a name="maintaining-an-installation"></a>Обслуживание установки
 Если открыть **Панель управления** и снова запустить приложение установки, можно изменить компоненты Visual Studio, удалить языки программирования, а также восстановить или удалить Visual Studio.

> [!NOTE]
> Для запуска программы установки в режиме обслуживания пользователь должен обладать полномочиями администратора на локальном компьютере.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Обслуживание установки на клиентском компьютере

- Откройте **Панель управления**и выберите **Программы и компоненты**.

- Выберите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], затем выберите **Изменить**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Изменение параметров AdminDeployment на клиентском компьютере после установки Visual Studio

1. Обновите файл AdminDeployment.xml по мере необходимости.

2. Нажмите кнопку **Пуск** и выберите **Выполнить**.

3. Введите следующий текст: \\\\*имя_сервера*\IDEinstall\vs_*продукт*.exe /AdminFile путь_к_файлу_Admindeployment.xml

    ДополнительныеПараметрыПоМереНеобходимости

    Например, можно указать следующую командную строку: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Восстановление является параметром по умолчанию после установки Visual Studio. При восстановлении Visual Studio с использованием обновленного параметра /AdminFile текущие параметры развертывания администратора будут переопределены теми, которые вызываются обновленным файлом AdminDeployment.xml.

## <a name="updating-an-installation"></a>Обновление установки
 Корпорация Майкрософт выпустила несколько обновлений для Visual Studio 2015. В этом разделе описывается, как обновить образ автоматической установки Visual Studio 2015 для включения обновлений.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Чтобы обновить автоматическую установку Visual Studio, сделайте следующее:

1. Найдите файл продукт.exe в существующем сетевом образе, щелкните его правой кнопкой мыши и выберите **Свойства**.

2. Откройте вкладку **Подробные сведения** и запишите значение свойства **Версия продукта**.

    ![Пример диалогового окна "Свойства" в автоматической установке Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "Автоматическая установка-диалоговое окно "Свойства"")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Если продукт имеет версию 14.0.24720.0 или 14.0.24720.1, выполните следующие шаги:
   1. Выполните команду *продукт.exe* /Layout *диск:* \IDEinstall на компьютере с доступом к Интернету. (Например, выполните команду `vs_enterprise.exe /Layout d:\IDEinstall`.)

   2. После завершения работы /Layout скопируйте новый образ в новое расположение.

   3. Создайте и измените файл AdminDeployment.xml. Для этого используйте `/CreateAdminFile` *\<file location>* параметр командной строки. (См. подробнее о развертывании Visual Studio в автоматическом режиме в этой статье.)

   4. На клиентском компьютере выполните следующую команду, чтобы обновить копию Visual Studio, которую вы установили ранее: \\\\*сервер1*\IDEinstall_Updated_1\\*продукт.exe* /adminfile \\\сервер1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart.

        Например, выполните команду `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Для других версий продукта выполните следующие шаги:
   1. Выполните команду *продукт.exe* /Layout *диск:* \IDEinstall на компьютере с доступом к Интернету. (Например, выполните команду `vs-enterprise.exe /Layout d:\IDEinstall`.)

   2. После завершения работы /Layout скопируйте новый образ в новое расположение. (Или вы можете переопределить существующий сетевой образ.)

   3. Создайте и измените файл AdminDeployment.xml. Для этого используйте `/CreateAdminFile` *\<file location>* параметр командной строки. (См. подробнее о развертывании Visual Studio в автоматическом режиме в этой статье.)

   4. Если вы скопировали образ в новое расположение, вам нужно выполнить следующую команду на клиентском компьютере, чтобы обновить копию Visual Studio, которую вы установили ранее: \\\\*сервер1*\IDEinstall_Updated_1\\*продукт.exe* /adminfile \\\сервер1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart.

        Например, выполните команду `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. Если вы переопределили существующий сетевой образ, вы можете выполнить команду, указанную в предыдущем шаге, или сделать следующее:
       1. Откройте **Панель управления**и выберите **Программы и компоненты**.

       2. Выберите **Visual Studio** и **Изменить**.

       3. Когда Visual Studio запустится в режиме обслуживания, щелкните **Изменить**.

       4. Последнее обновление отобразится на странице компонентов. Выберите другие компоненты, которые нужно установить, нажмите кнопку **Далее** и выберите **Обновить**, чтобы установить обновление и новые компоненты.

## <a name="registering-the-product"></a>Регистрация продукта
 После завершения установки вы можете зарегистрировать свою копию [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прямо из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>Для регистрации выполните следующие команды.

1. В меню **Справка** выберите **Зарегистрировать продукт**.

2. Введите ключ продукта.

     (См. подробнее о [поиске ключа продукта Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) и [автоматическом применении ключей продукта при развертывании Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).)

## <a name="see-also"></a>См. также:
 [Установка Visual Studio](../install/install-visual-studio-2015.md)