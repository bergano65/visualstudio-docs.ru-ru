---
title: Установка Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a31bc328c20aada21b05edeef61886d57e914165
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298050"
---
# <a name="install-visual-studio-2015"></a>Установка Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта страница содержит подробные сведения, которые помогут вам в установке **Visual Studio 2015** — нашего интегрированного набора инструментов для повышения производительности разработчиков. Также включены ссылки на сведения о [компонентах](https://www.visualstudio.com/news/vs2015-vs.aspx), [выпусках](https://go.microsoft.com/fwlink/?LinkID=242142), [требованиях к системе](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [скачиваемых материалах](https://go.microsoft.com/fwlink/?LinkId=517106)и многом другом.

## <a name="quick-links"></a>Полезные ссылки

Прежде чем мы углубимся в детали, см. список наиболее часто запрашиваемых ссылок, приведенный ниже.

|||
|------------------|----------------|
|![Скачать Visual Studio 2012](../install/media/downloads.png "Загрузки") |**Downloads**: To install Visual Studio 2015, you can download a product executable file from the  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page (subscription required), or use the installation media from the boxed product. [Learn more about how to download current or previous versions of Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Learn more about features](../install/media/features.png "Компоненты") |**Features**: To learn  more about the features in Visual Studio 2015, see the release notes for [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs), and [Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Find out what's in each SKU](../install/media/sku.png "Номера SKU") |**Номера SKU**: чтобы узнать, какие компоненты и функции доступны в каждом выпуске Visual Studio 2015, посетите страницу [Сравнение предложений Visual Studio](https://go.microsoft.com/fwlink/?LinkID=242142).|
|![View system requirements](../install/media/system-requirements.png "Требования к системе") |**System Requirements**: To view the system requirements for each edition of Visual Studio 2015, see the [Visual Studio 2015 Compatibility](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) page.|
|![Locate your Product Key](../install/media/product-keys.png "Ключи продукта") |**Product Keys**: To locate your product key, see the [How to: Locate the Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) topic.|
|![Find out about licensing](../install/media/licensing.png "Лицензирование") |**Licensing**: To find out about licensing options for both individuals or enterprise customers, see  the [Visual Studio and MSDN Licensing](https://www.microsoft.com/download/details.aspx?id=13350) white paper.|

## <a name="custom"></a> Default vs. Custom Setup
 При установке Visual Studio 2015 можно включать или исключать компоненты в зависимости от того, насколько часто вы предполагаете их использовать. Это означает, что установка по умолчанию, как правило, требует меньше места и происходит быстрее, чем выборочная установка. Кроме того, это означает, что многие компоненты, которые устанавливались в предыдущих версиях по умолчанию, в этой версии считаются настраиваемыми компонентами, которые требуется явно выбирать для установки.

 ![Visual Studio 2015 Setup Dialog](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Настраиваемые компоненты включают Visual C++, Visual F#, SQL Server Data Tools, пакеты SDK и средства разработки кроссплатформенных мобильных приложений, а также сторонние пакеты SDK и расширения. Если вы не выбрали эти компоненты во время начальной установки, вы можете установить их позднее.

> [!NOTE]
> Выборочная установка автоматически включает компоненты установки по умолчанию.

 Ниже приведен полный список настраиваемых компонентов.

|Feature Sets|Компоненты|
|------------------|----------------|
|**Обновления**|Visual Studio 2015 с обновлением 3|
|**Языки программирования**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Разработка для Windows и веб-разработка**|Средства публикации ClickOnce<br />LightSwitch<br />Инструменты разработчика Microsoft Office<br />Microsoft SQL Server Data Tools<br /> Веб-инструменты Майкрософт для разработчиков<br />PowerShell Tools for Visual Studio (3rd Party)<br />Набор разработки для Silverlight<br />Средства разработки универсальных приложений Windows<br />Средства и пакеты SDK Windows 10<br />Средства Windows 8.1 и Windows Phone 8.0/8.1<br />Средства и пакеты SDK Windows 8.1|
|**Разработка кроссплатформенных мобильных приложений**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Разработка мобильных приложений Visual C++ для iOS и Android<br />Clang с Microsoft CodeGen|
|**Common Tools and Software Development Kits**|Android Native Development Kit (3rd Party)<br /> Android SDK [3rd Party]<br />Android SDK Setup APIs (3rd Party)<br />Apache Ant (3rd Party)<br /> Java SE Development Kit (3rd Party)<br /> Joyent Node.js (3rd Party)|
|**Общие средства**|Git for Windows (3rd Party)<br />GitHub Extension for Visual Studio (3rd Party)<br /> Средства расширения Visual Studio|

## <a name="installing"></a> Установка Visual Studio
 You can install Visual Studio by using installation media (DVDs), by using your Visual Studio subscription service from the [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) website, by downloading  a web installer from the [Visual Studio Downloads](https://go.microsoft.com/fwlink/?LinkId=517106) website, or by creating an offline installation layout (see the [Create an Offline Installation of Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page for more details).

> [!IMPORTANT]
> Установка [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]должна выполняться от имени учетной записи администратора. Тем не менее для работы с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] после установки они не нужны.

 Для установки всех компонентов Visual Studio учетной записи локального администратора необходимо предоставить следующие права.

|Отображаемое имя объекта локальной политики|Право пользователя|
|--------------------------------------|----------------|
|Резервное копирование файлов и каталогов|SeBackupPrivilege|
|Отладка программ|SeBackupPrivilege|
|Управление аудитом и журналом безопасности|SeSecurityPrivilege|

 Более подробную информацию о требованиях к учетной записи локального администратора см. в статье базы знаний [Установка SQL Server завершается ошибкой, если учетная запись для установки не имеет определенных прав пользователя](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a> Using installation media
 Чтобы установить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], в корневом каталоге установочного носителя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запустите файл установки для нужного выпуска:

|Выпуск|Файл установки|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="BKMK_Website"></a> Downloading from the product website
 Visit the [Visual Studio Downloads](https://go.microsoft.com/fwlink/?LinkId=517106) page, and select the edition of Visual Studio that you want.

### <a name="downloading-from-your-subscription-service"></a>Downloading from your subscription service
 Visit  the [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page, and select the edition of Visual Studio that you want.

### <a name="BKMK_Offline"></a> Creating an offline installation layout
 If you do not have the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installation media, or you do not have a Visual Studio subscription,  or you do not want to install [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] by using the web installer, you can perform a "disconnected" installation by creating what is known as an offline installation layout. For more information, see the [Create an Offline Installation of Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page.

## <a name="enterprise"></a> Deploying Visual Studio in an Enterprise
 For information about how to deploy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] over a network, see the [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a> Installing Visual Studio in a virtualized environment
 **Проблемы, связанные с видео, при использовании Hyper-V**

 В случае использования Windows Server 2008 R2 с Hyper-V и графическим ускорителем, система может работать медленнее, чем обычно.

 Более подробную информацию см. на следующей странице веб-сайта Майкрософт: [Видео может снизить производительность на компьютерах с Windows Server 2008 и Windows Server 2008 R2 с включенной ролью Hyper-V и установленным ускорителем адаптера дисплея](https://go.microsoft.com/fwlink/?LinkID=231084).

 **Эмуляция устройств с помощью Hyper-V**

 При установке Visual Studio 2015 на реальном оборудовании без виртуализации можно выбрать компоненты, обеспечивающие эмуляцию устройств Windows и Android с помощью Hyper-V. При установке в Hyper-V эмуляция устройств Windows или Android недоступна. Это связано с тем, что эмуляторы являются виртуальными машинами сами по себе, а размещать одну виртуальную машину внутри другой на данный момент нельзя. Эту проблему можно решить, развернув и отладив приложение на реальном устройстве Windows или Android.

## <a name="optionalComponents"></a> Installing optional components
 If you want to install components that you might not have selected during your original installation, use the following procedure.

#### <a name="to-install-optional-components"></a>To install optional components

1. На странице **Программы и компоненты** **панели управления** выберите выпуск продукта, в который требуется добавить один или более компонентов, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Изменить**, а затем выберите компоненты, которые необходимо установить.

3. Нажмите кнопку **Далее**, а затем следуйте инструкциям.

## <a name="helpContent"></a> Установка содержимого автономной справки
 После установки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]можно скачать дополнительное содержимое справки, чтобы сделать его доступным в автономном режиме.

#### <a name="to-install-or-uninstall-help-content"></a>Установка и удаление содержимого справки

1. В строке меню [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] выберите **Справка**, **Добавление и удаление содержимого справки**.

2. На вкладке **Управление содержимым** **средства просмотра справки (Майкрософт)** выберите источник установки для содержимого справки.

3. При поиске определенной коллекции справки введите ключевое слово или имя в текстовое поле **Поиск** и нажмите клавишу **ВВОД**.

4. Щелкните ссылку **Добавить** или **Удалить** рядом с именем нужной коллекции справки.

5. Нажмите кнопку **Обновить**.

   For more information about how to install or deploy offline Help, see the [Help Viewer Administrator Guide](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a> Проверка наличия исправлений и обновлений
 Visual Studio не обновляет расширения автоматически при обновлении с предыдущих версий, так как не все расширения совместимы. You must reinstall the extensions from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/) or from the software publisher.

#### <a name="to-automatically-check-for-service-releases"></a>Автоматическая проверка наличия наборов исправлений

1. В строке меню выберите **Сервис**, **Параметры**.

2. В диалоговом окне **Параметры** раскройте элемент **Среда**, а затем выберите **Расширения и обновления**. Убедитесь, что установлен флажок **Автоматически проверять наличие обновлений** и нажмите кнопку **ОК**.

## <a name="registering-visual-studio"></a>Регистрация Visual Studio

1. В строке меню выберите **Справка**, **О программе**.

     Диалоговое окно **О программе** содержит идентификационный номер продукта (PID). Для регистрации продукта необходимо указать PID и данные учетной записи Windows (например, адрес и пароль электронной почты на Hotmail или Outlook.com).

2. В меню **Справка**выберите команду **Зарегистрировать продукт**.

## <a name="repair"></a> Восстановление Visual Studio

#### <a name="to-repair-visual-studio"></a>Восстановление Visual Studio

1. На странице **Программы и компоненты** **панели управления** выберите выпуск продукта, который необходимо восстановить, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Восстановить**, нажмите кнопку **Далее**, а затем следуйте инструкциям.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>To repair Visual Studio in silent or passive modes (that is, to repair from source)

1. На компьютере, на котором установлена среда Visual Studio, откройте командную строку Windows.

2. Введите следующие параметры:

     *DVDRoot* \\<Installation File\> \</quiet&#124;/passive> [/norestart]/Repair

## <a name="troubleshooting"></a> Troubleshooting an installation
 Используйте следующие ресурсы, чтобы получить помощь в разрешении проблем настройки и установки:

- Форум по[установке и настройке Visual Studio](https://go.microsoft.com/fwlink/?LinkID=151190) . Просмотрите вопросы и ответы от других пользователей сообщества Visual Studio. Если вы не нашли нужную информацию, задайте собственные вопросы.

- Веб-сайт[службы поддержки Майкрософт для Visual Studio](https://go.microsoft.com/fwlink/?LinkID=251019) . Прочтите статьи базы знаний (KB) и узнайте, как связаться со службой поддержкой корпорации Майкрософт по вопросам установки Visual Studio.

## <a name="relatedTopics"></a> Связанные разделы

|Заголовок|Описание|
|-----------|-----------------|
|[Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Describes how to install Visual Studio when you are not connected to the Internet.
|[Параллельная установка версий Visual Studio](../install/install-visual-studio-versions-side-by-side.md)|Сведения об установке и использовании нескольких версий Visual Studio на одном компьютере.|
|[Использование параметров командной строки для установки Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Lists the command-line parameters that you can use when you install Visual Studio from a command prompt.|
|[Удаление Visual Studio](../install/uninstall-visual-studio.md)|Describes how to uninstall Visual Studio.|
|[Руководство администратора Visual Studio](../install/visual-studio-administrator-guide.md)|Сведения о вариантах развертывания Visual Studio.|
|[Библиотека изображений Visual Studio](../designers/the-visual-studio-image-library.md)|Сведения об установке графики, которая может использоваться в приложениях Visual Studio.|
|[Начало разработки в Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Includes information and links that can help you use Visual Studio more effectively.|

## <a name="see-also"></a>См. также раздел

- [Вход в Visual Studio](../ide/signing-in-to-visual-studio.md)