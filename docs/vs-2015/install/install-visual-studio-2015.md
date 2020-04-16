---
title: Установка Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 04/15/2020
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
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445081"
---
# <a name="install-visual-studio-2015"></a>Установка Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта страница содержит подробные сведения, которые помогут вам в установке **Visual Studio 2015** — нашего интегрированного набора инструментов для повышения производительности разработчиков. Мы также включили ссылки, чтобы быстро получить информацию о [функциях,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history) [системных требований,](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs)загрузок и многое [другое.](https://visualstudio.microsoft.com/vs/older-downloads/)

## <a name="quick-links"></a>Полезные ссылки

Прежде чем мы углубимся в детали, см. список наиболее часто запрашиваемых ссылок, приведенный ниже.

|||
|------------------|----------------|
|![Скачать Visual Studio](../install/media/downloads.png "Загрузки") |**Загрузки**: Для установки Visual Studio 2015, вы можете скачать продукт исполняемый файл с [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) страницы (требуется подписка), или использовать установку мультимедиа из коробочного продукта. [Узнайте больше о том, как скачать текущие или предыдущие версии Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Подробнее о функциях](../install/media/features.png "Компоненты") |**Особенности**: Чтобы узнать больше об особенностях в Visual Studio 2015, см. примечания к выпуску для [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Обновление 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Обновление 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs), и [обновление 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Просмотр требований системы](../install/media/system-requirements.png "Требования к системе") |**Системные требования**: Для просмотра системных требований для каждого издания Visual Studio 2015, [см.](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)|
|![Найдите ключ к продукту](../install/media/product-keys.png "Ключи продукта") |**Продукт Ключи**: Чтобы найти ваш продукт ключ, см [Как: Найдите Visual Studio Продукт Ключевые](../install/how-to-locate-the-visual-studio-product-key.md) темы.|
|![Узнайте о лицензировании](../install/media/licensing.png "Лицензирование") |**Лицензирование**: Чтобы узнать о вариантах лицензирования как для физических лиц, так и для корпоративных клиентов, [см.](https://www.microsoft.com/download/details.aspx?id=13350)|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>По умолчанию против пользовательской настройки
 При установке Visual Studio 2015 можно включать или исключать компоненты в зависимости от того, насколько часто вы предполагаете их использовать. Это означает, что установка по умолчанию, как правило, требует меньше места и происходит быстрее, чем выборочная установка. Кроме того, это означает, что многие компоненты, которые устанавливались в предыдущих версиях по умолчанию, в этой версии считаются настраиваемыми компонентами, которые требуется явно выбирать для установки.

 ![Диалоговое окно установки Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Пользовательские компоненты включают в себя визуальные СЗ, Визуальный F, S'L Server Data Tools, кросс-платформенные мобильные инструменты и SDK, а также сторонние SDK и расширения. Если вы не выбрали эти компоненты во время начальной установки, вы можете установить их позднее.

> [!NOTE]
> Выборочная установка автоматически включает компоненты установки по умолчанию.

 Ниже приведен полный список настраиваемых компонентов.

|Наборы функций|Components|
|------------------|----------------|
|**Обновления**|Visual Studio 2015 с обновлением 3|
|**Языки программирования**|Visual C++<br />Visual F#;<br />Средства Python для Visual Studio|
|**Разработка для Windows и веб-разработка**|Средства публикации ClickOnce<br />LightSwitch<br />Инструменты разработчика Microsoft Office<br />Microsoft SQL Server Data Tools<br /> Веб-инструменты Майкрософт для разработчиков<br />Инструменты PowerShell для визуальной студии (3-я партия)<br />Набор разработки для Silverlight<br />Средства разработки универсальных приложений Windows<br />Средства и пакеты SDK Windows 10<br />Средства Windows 8.1 и Windows Phone 8.0/8.1<br />Средства и пакеты SDK Windows 8.1|
|**Разработка кроссплатформенных мобильных приложений**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Разработка мобильных приложений Visual C++ для iOS и Android<br />Clang с Microsoft CodeGen|
|**Общие инструменты и наборы для разработки программного обеспечения**|Набор для развития Android Родной (3-я партия)<br /> Андроид SDK (3-я партия)<br />Android SDK Setup AIS (3-я партия)<br />Апач Ант (3-я партия)<br /> Комплект разработки Java SE (3-я партия)<br /> Joyent Node.js (3-я партия)|
|**Общие средства**|Git для Windows (3-я партия)<br />Расширение GitHub для визуальной студии (3-я партия)<br /> Средства расширения Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a>Установка визуальной студии
 Вы можете установить Visual Studio с помощью установки мультимедиа (DVDs), используя службу подписки Visual Studio с [веб-сайта My.VisualStudio.com,](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) загрузив веб-установщик с веб-сайта [Visual Studio Downloads](https://visualstudio.microsoft.com/vs/older-downloads/) или создав автономный макет установки (см. [Создать оффлайн-установку](../install/create-an-offline-installation-of-visual-studio.md) visual Studio для более подробной информации).

> [!IMPORTANT]
> Установка [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]должна выполняться от имени учетной записи администратора. Тем не менее для работы с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] после установки они не нужны.

 Для установки всех компонентов Visual Studio учетной записи локального администратора необходимо предоставить следующие права.

|Отображаемое имя объекта локальной политики|Право пользователя|
|--------------------------------------|----------------|
|Резервное копирование файлов и каталогов|SeBackupPrivilege|
|Отладка программ|SeBackupPrivilege|
|Управление аудитом и журналом безопасности|SeSecurityPrivilege|

 Более подробную информацию о требованиях к учетной записи локального администратора см. в статье базы знаний [Установка SQL Server завершается ошибкой, если учетная запись для установки не имеет определенных прав пользователя](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Использование носителей установки
 Чтобы установить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], в корневом каталоге установочного носителя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запустите файл установки для нужного выпуска:

|Выпуск|Файл установки|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Скачать с веб-сайта продукта
 Посетите страницу [Visual Studio Downloads](https://visualstudio.microsoft.com/vs/older-downloads/) и выберите нужное издание Visual Studio.

### <a name="download-from-your-subscription-service"></a>Скачать из службы подписки
 Посетите страницу [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) и выберите издание Visual Studio, которое вы хотите.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Создание автономного макета установки
 Если у вас [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] нет носителя установки, или у вас нет подписки Visual [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Studio, или вы не хотите установить с помощью веб-установщика, вы можете выполнить "отключенную" установку, создав так называемое автономное расположение установки. Для получения дополнительной информации смотрите [страницу «Создай в автономном режиме»](../install/create-an-offline-installation-of-visual-studio.md) visual Studio.

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Развертывание визуальной студии на предприятии
 Для получения информации [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] о том, как развернуть по сети, см. [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md)

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Установка Visual Studio в виртуализированной среде
 **Проблемы, связанные с видео, при использовании Hyper-V**

 В случае использования Windows Server 2008 R2 с Hyper-V и графическим ускорителем, система может работать медленнее, чем обычно.

 Для получения дополнительной информации, [см. Видео производительность может снизиться, когда Windows Server 2008 или Windows Server 2008 R2 на основе компьютера имеет роль Hyper-V включен и ускоренный адаптер дисплея установлен.](https://support.microsoft.com/kb/961661)

 **Эмуляция устройств с помощью Hyper-V**

 При установке Visual Studio 2015 на реальном оборудовании без виртуализации можно выбрать компоненты, обеспечивающие эмуляцию устройств Windows и Android с помощью Hyper-V. При установке в Hyper-V эмуляция устройств Windows или Android недоступна. Это связано с тем, что эмуляторы являются виртуальными машинами сами по себе, а размещать одну виртуальную машину внутри другой на данный момент нельзя. Эту проблему можно решить, развернув и отладив приложение на реальном устройстве Windows или Android.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>Установка дополнительных компонентов
 Если вы хотите установить компоненты, которые вы, возможно, не выбрали во время первоначальной установки, используйте следующую процедуру.

#### <a name="to-install-optional-components"></a>Установка дополнительных компонентов

1. На странице **Программы и компоненты****панели управления** выберите выпуск продукта, в который требуется добавить один или более компонентов, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Изменить**, а затем выберите компоненты, которые необходимо установить.

3. Нажмите кнопку **Далее**, а затем следуйте инструкциям.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Установка содержимого справки в автономном режиме
 После установки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]можно скачать дополнительное содержимое справки, чтобы сделать его доступным в автономном режиме.

#### <a name="to-install-or-uninstall-help-content"></a>Установка и удаление содержимого справки

1. В строке меню [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] выберите **Справка**, **Добавление и удаление содержимого справки**.

2. На вкладке **Управление содержимым****средства просмотра справки (Майкрософт)** выберите источник установки для содержимого справки.

3. При поиске определенной коллекции справки введите ключевое слово или имя в текстовое поле **Поиск** и нажмите клавишу **ВВОД**.

4. Щелкните ссылку **Добавить** или **Удалить** рядом с именем нужной коллекции справки.

5. Нажмите кнопку **Обновить**.

   Для получения дополнительной информации о том, как установить или развернуть в автономном режиме Справка, смотрите [Руководство администратора просмотра справки](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Проверка на наличие сервисных релизов и обновлений продуктов
 Visual Studio не обновляет расширения автоматически при обновлении с предыдущих версий, так как не все расширения совместимы. Вы должны переустановить расширения из [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или от издателя программного обеспечения.

#### <a name="to-automatically-check-for-service-releases"></a>Автоматическая проверка наличия наборов исправлений

1. В меню бар, выбрать **инструменты**, **Варианты**.

2. В диалоговом окне **Параметры** раскройте элемент **Среда**, а затем выберите **Расширения и обновления**. Убедитесь, что установлен флажок **Автоматически проверять наличие обновлений** и нажмите кнопку **ОК**.

## <a name="register-visual-studio"></a>Регистрация визуальной студии

1. В строке меню выберите **Справка**, **О программе**.

     Диалоговое окно **О программе** содержит идентификационный номер продукта (PID). Для регистрации продукта необходимо указать PID и данные учетной записи Windows (например, адрес и пароль электронной почты на Hotmail или Outlook.com).

2. В меню **Справка**выберите команду **Зарегистрировать продукт**.

## <a name="repair-visual-studio"></a><a name="repair"></a>Ремонт Визуальной студии

#### <a name="to-repair-visual-studio"></a>Восстановление Visual Studio

1. На странице **Программы и компоненты****панели управления** выберите выпуск продукта, который необходимо восстановить, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Восстановить**, нажмите кнопку **Далее**, а затем следуйте инструкциям.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Для ремонта Visual Studio в бесшумных или пассивных режимах (то есть, для ремонта из источника)

1. На компьютере, на котором установлена среда Visual Studio, откройте командную строку Windows.

2. Задайте следующие параметры:

     *DVDRoot* \\ < *Установка файла* \> \< `/quiet|/passive`>`norestart``Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Устранение неполадок установки
 Используйте следующие ресурсы, чтобы получить помощь в разрешении проблем настройки и установки:

- Форум по[установке и настройке Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Просмотрите вопросы и ответы от других пользователей сообщества Visual Studio. Если вы не нашли нужную информацию, задайте собственные вопросы.

- [Получите помощь в Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Найдите статьи базы знаний (KB) и узнайте, как связаться с службой поддержки Майкрософт для получения информации о проблемах с установкой Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a>Похожие темы

|Title|Описание|
|-----------|-----------------|
|[Создание автономной установки визуальной студии](../install/create-an-offline-installation-of-visual-studio.md)|Описывает, как установить Visual Studio, когда вы не подключены к Интернету.
|[Установка визуальных версий студии бок о бок](../install/install-visual-studio-versions-side-by-side.md)|Сведения об установке и использовании нескольких версий Visual Studio на одном компьютере.|
|[Используйте параметры командной строки для установки визуальной студии](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Перечисляет параметры командной строки, которые можно использовать при установке Visual Studio из командного запроса.|
|[Удаление Visual Studio](../install/uninstall-visual-studio.md)|Описывает, как удалить Visual Studio.|
|[Визуальная студия Администратор Руководство](../install/visual-studio-administrator-guide.md)|Сведения о вариантах развертывания Visual Studio.|
|[Библиотека изображений визуальной студии](../designers/the-visual-studio-image-library.md)|Сведения об установке графики, которая может использоваться в приложениях Visual Studio.|
|[Начало разработки с visual Studio](../ide/get-started-developing-with-visual-studio.md)|Включает информацию и ссылки, которые могут помочь вам использовать Visual Studio более эффективно.|

## <a name="see-also"></a>См. также:

- [Вход в Visual Studio](../ide/signing-in-to-visual-studio.md)
