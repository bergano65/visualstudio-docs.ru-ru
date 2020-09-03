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
ms.openlocfilehash: d593625985924d8c8076e1bdd361ce4d08c1dfbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548048"
---
# <a name="install-visual-studio-2015"></a>Установка Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта страница содержит подробные сведения, которые помогут вам в установке **Visual Studio 2015** — нашего интегрированного набора инструментов для повышения производительности разработчиков. Мы также включили ссылки для быстрого получения сведений о [компонентах](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), [требованиях к системе](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [файлах для загрузки](https://visualstudio.microsoft.com/vs/older-downloads/)и многом другое.

## <a name="quick-links"></a>Полезные ссылки

Прежде чем мы углубимся в детали, см. список наиболее часто запрашиваемых ссылок, приведенный ниже.

|Заголовок|Описание|
|------------------|----------------|
|![Скачать Visual Studio 2012](../install/media/downloads.png "Файлы для загрузки") |**Загрузки**. для установки Visual Studio 2015 можно загрузить исполняемый файл продукта со страницы  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (требуется подписка) или использовать установочный носитель из продукта в штучной упаковке. [Узнайте больше о том, как скачать текущую или предыдущую версию Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Дополнительные сведения о функциях](../install/media/features.png "Компоненты") |**Компоненты**. Дополнительные сведения о функциях Visual Studio 2015 см. в заметках о выпуске [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Обновление 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Обновление 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)и [Обновление 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Просмотр требований к системе](../install/media/system-requirements.png "Требования к системе") |**Требования к системе**. сведения о требованиях к системе для каждого выпуска visual Studio 2015 см. на странице [Целевая платформа и совместимость для Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Определение ключа продукта](../install/media/product-keys.png "Ключи продуктов") |**Ключи продуктов**. чтобы найти ключ продукта, см. раздел [как найти ключ продукта Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Сведения о лицензировании](../install/media/licensing.png "Лицензирование") |**Лицензирование**. сведения о вариантах лицензирования для отдельных пользователей или корпоративных клиентов см. в [техническом документе о лицензировании Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a> По умолчанию и Выборочная установка
 При установке Visual Studio 2015 можно включать или исключать компоненты в зависимости от того, насколько часто вы предполагаете их использовать. Это означает, что установка по умолчанию, как правило, требует меньше места и происходит быстрее, чем выборочная установка. Кроме того, это означает, что многие компоненты, которые устанавливались в предыдущих версиях по умолчанию, в этой версии считаются настраиваемыми компонентами, которые требуется явно выбирать для установки.

 ![Диалоговое окно установки Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 К настраиваемым компонентам относятся Visual C++, Visual F#, SQL Server Data Tools, кросс-платформенные мобильные средства и пакеты SDK, а сторонние пакеты SDK и расширения. Если вы не выбрали эти компоненты во время начальной установки, вы можете установить их позднее.

> [!NOTE]
> Выборочная установка автоматически включает компоненты установки по умолчанию.

 Ниже приведен полный список настраиваемых компонентов.

|Наборы функций|Компоненты|
|------------------|----------------|
|**Обновления**|Visual Studio 2015 с обновлением 3|
|**Языки программирования**|Visual C++<br />Visual F#<br />Средства Python для Visual Studio|
|**Разработка для Windows и веб-разработка**|Средства публикации ClickOnce<br />LightSwitch<br />Инструменты разработчика Microsoft Office<br />Microsoft SQL Server Data Tools<br /> Веб-инструменты Майкрософт для разработчиков<br />PowerShell Tools for Visual Studio (третья сторона)<br />Набор разработки для Silverlight<br />Средства разработки универсальных приложений Windows<br />Средства и пакеты SDK Windows 10<br />Средства Windows 8.1 и Windows Phone 8.0/8.1<br />Средства и пакеты SDK Windows 8.1|
|**Разработка кроссплатформенных мобильных приложений**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Разработка мобильных приложений Visual C++ для iOS и Android<br />Clang с Microsoft CodeGen|
|**Общие средства и пакеты средств разработки программного обеспечения**|Пакет Android Native Development Kit (третья сторона)<br /> Пакет SDK для Android [третья сторона]<br />API-интерфейсы установки пакет SDK для Android (третья сторона)<br />Apache Ant (третья сторона)<br /> Пакет SDK для Java SE (третья сторона)<br /> Node.js жойент (третья сторона)|
|**Общие средства**|Git для Windows (третья сторона)<br />Расширение GitHub для Visual Studio (третья сторона)<br /> Средства расширения Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a> Установка Visual Studio
 Вы можете установить Visual Studio с помощью установочного носителя (DVD), используя службу подписки Visual Studio на веб-сайте [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , загрузив веб-установщик с веб-сайта [загрузки Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) или создав автономный макет установки (Дополнительные сведения см. в разделе [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ).

> [!IMPORTANT]
> Установка [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]должна выполняться от имени учетной записи администратора. Тем не менее для работы с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] после установки они не нужны.

 Для установки всех компонентов Visual Studio учетной записи локального администратора необходимо предоставить следующие права.

|Отображаемое имя объекта локальной политики|Право пользователя|
|--------------------------------------|----------------|
|Резервное копирование файлов и каталогов|SeBackupPrivilege|
|Отладка программ|SeBackupPrivilege|
|Управление аудитом и журналом безопасности|SeSecurityPrivilege|

 Более подробную информацию о требованиях к учетной записи локального администратора см. в статье базы знаний [Установка SQL Server завершается ошибкой, если учетная запись для установки не имеет определенных прав пользователя](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a> Использовать установочный носитель
 Чтобы установить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], в корневом каталоге установочного носителя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запустите файл установки для нужного выпуска:

|выпуск|Файл установки|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a> Загрузка с веб-сайта продукта
 Перейдите на страницу [загрузки Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) и выберите нужный выпуск Visual Studio.

### <a name="download-from-your-subscription-service"></a>Скачивание из службы подписки
 Перейдите на страницу [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) и выберите нужный выпуск Visual Studio.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a> Создание макета автономной установки
 Если у вас нет [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установочного носителя или у вас нет подписки Visual Studio или вы не хотите устанавливать [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с помощью веб-установщика, можно выполнить «отключенную» установку, создав автономный режим установки. Дополнительные сведения см. на странице [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a> Развертывание Visual Studio на предприятии
 Дополнительные сведения о развертывании [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] по сети см. в разделе [Руководство администратора Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a> Установка Visual Studio в виртуализированной среде
 **Проблемы, связанные с видео, при использовании Hyper-V**

 В случае использования Windows Server 2008 R2 с Hyper-V и графическим ускорителем, система может работать медленнее, чем обычно.

 Дополнительные сведения см. в разделе [производительность видео может снизиться, если на компьютере под управлением Windows server 2008 или Windows server 2008 R2 включена роль Hyper-V и установлен адаптер ускоренного дисплея](https://support.microsoft.com/kb/961661).

 **Эмуляция устройств с помощью Hyper-V**

 При установке Visual Studio 2015 на реальном оборудовании без виртуализации можно выбрать компоненты, обеспечивающие эмуляцию устройств Windows и Android с помощью Hyper-V. При установке в Hyper-V эмуляция устройств Windows или Android недоступна. Это связано с тем, что эмуляторы являются виртуальными машинами сами по себе, а размещать одну виртуальную машину внутри другой на данный момент нельзя. Эту проблему можно решить, развернув и отладив приложение на реальном устройстве Windows или Android.

## <a name="install-optional-components"></a><a name="optionalComponents"></a> Установка дополнительных компонентов
 Если вы хотите установить компоненты, которые могут быть не выбраны во время первоначальной установки, выполните следующую процедуру.

#### <a name="to-install-optional-components"></a>Установка дополнительных компонентов

1. На странице **Программы и компоненты****панели управления** выберите выпуск продукта, в который требуется добавить один или более компонентов, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Изменить**, а затем выберите компоненты, которые необходимо установить.

3. Нажмите кнопку **Далее**, а затем следуйте инструкциям.

## <a name="install-offline-help-content"></a><a name="helpContent"></a> Установка автономного содержимого справки
 После установки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]можно скачать дополнительное содержимое справки, чтобы сделать его доступным в автономном режиме.

#### <a name="to-install-or-uninstall-help-content"></a>Установка и удаление содержимого справки

1. В строке меню [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] выберите **Справка**, **Добавление и удаление содержимого справки**.

2. На вкладке **Управление содержимым****средства просмотра справки (Майкрософт)** выберите источник установки для содержимого справки.

3. При поиске определенной коллекции справки введите ключевое слово или имя в текстовое поле **Поиск** и нажмите клавишу **ВВОД**.

4. Щелкните ссылку **Добавить** или **Удалить** рядом с именем нужной коллекции справки.

5. Нажмите кнопку **Обновить**.

   Дополнительные сведения об установке и развертывании автономной справки см. в разделе [Руководство администратора окна справки](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a> Проверка наличия выпусков обновлений и продуктов
 Visual Studio не обновляет расширения автоматически при обновлении с предыдущих версий, так как не все расширения совместимы. Расширения необходимо переустановить из [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или из издателя программного обеспечения.

#### <a name="to-automatically-check-for-service-releases"></a>Автоматическая проверка наличия наборов исправлений

1. В строке меню выберите **Сервис**, **Параметры**.

2. В диалоговом окне **Параметры** раскройте элемент **Среда**, а затем выберите **Расширения и обновления**. Убедитесь, что установлен флажок **Автоматически проверять наличие обновлений** и нажмите кнопку **ОК**.

## <a name="register-visual-studio"></a>Регистрация Visual Studio

1. В строке меню выберите **Справка**, **О программе**.

     Диалоговое окно **О программе** содержит идентификационный номер продукта (PID). Для регистрации продукта необходимо указать PID и данные учетной записи Windows (например, адрес и пароль электронной почты на Hotmail или Outlook.com).

2. В меню **Справка**выберите команду **Зарегистрировать продукт**.

## <a name="repair-visual-studio"></a><a name="repair"></a> Восстановление Visual Studio

#### <a name="to-repair-visual-studio"></a>Восстановление Visual Studio

1. На странице **Программы и компоненты****панели управления** выберите выпуск продукта, который необходимо восстановить, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Восстановить**, нажмите кнопку **Далее**, а затем следуйте инструкциям.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Восстановление Visual Studio в режиме молчания или пассивного режима (то есть для восстановления из источника)

1. На компьютере, на котором установлена среда Visual Studio, откройте командную строку Windows.

2. Задайте следующие параметры:

     *DVDRoot* \\ Двдрут < *Файл установки* \> \<`/quiet|/passive`> [/`norestart`]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a> Устранение неполадок при установке
 Используйте следующие ресурсы, чтобы получить помощь в разрешении проблем настройки и установки:

- Форум по[установке и настройке Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Просмотрите вопросы и ответы от других пользователей сообщества Visual Studio. Если вы не нашли нужную информацию, задайте собственные вопросы.

- [Получите справку по Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Найдите статьи базы знаний (KB) и Узнайте, как связаться с служба поддержки Майкрософт для получения сведений о проблемах с установкой Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a> См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Описание установки Visual Studio без подключения к Интернету.
|[Параллельная установка версий Visual Studio](../install/install-visual-studio-versions-side-by-side.md)|Сведения об установке и использовании нескольких версий Visual Studio на одном компьютере.|
|[Использование параметров командной строки для установки Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Выводит список параметров командной строки, которые можно использовать при установке Visual Studio в командной строке.|
|[Удаление Visual Studio](../install/uninstall-visual-studio.md)|Описание удаления Visual Studio.|
|[Руководством администратора Visual Studio](../install/visual-studio-administrator-guide.md)|Сведения о вариантах развертывания Visual Studio.|
|[Библиотека изображений Visual Studio](../designers/the-visual-studio-image-library.md)|Сведения об установке графики, которая может использоваться в приложениях Visual Studio.|
|[Приступая к разработке с помощью Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Содержит сведения и ссылки, которые могут помочь в более эффективном использовании Visual Studio.|

## <a name="see-also"></a>См. также:

- [Вход в Visual Studio](../ide/signing-in-to-visual-studio.md)
