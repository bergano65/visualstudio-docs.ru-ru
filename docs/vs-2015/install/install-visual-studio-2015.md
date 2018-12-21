---
title: Установка Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.openlocfilehash: 761264d80c04f0e2ce13a365071f56739d6961a2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055171"
---
# <a name="install-visual-studio-2015"></a>Установка Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта страница содержит подробные сведения, которые помогут вам в установке **Visual Studio 2015** — нашего интегрированного набора инструментов для повышения производительности разработчиков. Также включены ссылки на сведения о [компонентах](https://www.visualstudio.com/news/vs2015-vs.aspx), [выпусках](http://go.microsoft.com/fwlink/?LinkID=242142), [требованиях к системе](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [скачиваемых материалах](http://go.microsoft.com/fwlink/?LinkId=517106)и многом другом.

## <a name="quick-links"></a>Полезные ссылки

Прежде чем мы углубимся в детали, см. список наиболее часто запрашиваемых ссылок, приведенный ниже.

|||
|------------------|----------------|
|![Скачайте Visual Studio](../install/media/downloads.png "файлы для загрузки") |**Скачиваемые файлы** Чтобы установить Visual Studio 2015, можно загрузить исполняемый файл продукта из [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) странице (необходима подписка), или воспользуйтесь установочным носителем из коробочного продукта. [Дополнительные сведения о том, как загрузить текущие или предыдущие версии Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Дополнительные сведения о возможностях](../install/media/features.png "функции") |**Функции** Дополнительные сведения о функциях в Visual Studio 2015, см. заметки о выпуске [RTM](https://www.visualstudio.com/news/vs2015-vs), [с обновлением 1](https://www.visualstudio.com/news/vs2015-update1-vs), [с обновлением 2](https://www.visualstudio.com/news/vs2015-update2-vs), и [с обновлением 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Новые возможности в каждый номер SKU](../install/media/sku.png "номера SKU") |**Номера SKU**: чтобы узнать, какие компоненты и функции доступны в каждом выпуске Visual Studio 2015, посетите страницу [Сравнение предложений Visual Studio](http://go.microsoft.com/fwlink/?LinkID=242142).|
|![Просмотреть требования к системе](../install/media/system-requirements.png "требования к системе") |**Требования к системе**: чтобы просмотреть требования к системе для каждого выпуска Visual Studio 2015, посетите страницу [Совместимость Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs).|
|![Найдите ключ продукта](../install/media/product-keys.png "ключи продуктов") |**Ключи продуктов** Чтобы найти ключ продукта, см. в разделе [как: Найти ключ продукта Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) раздела.|
|![Узнайте о лицензировании](../install/media/licensing.png "лицензирования") |**Лицензирование**: чтобы ознакомиться с вариантами лицензирования для отдельных пользователей и корпоративных клиентов, обратитесь к документу [Лицензирование Visual Studio и MSDN](https://www.microsoft.com/download/details.aspx?id=13350).|

##  <a name="custom"></a> Установка по умолчанию и Выборочная установка
 При установке Visual Studio 2015 можно включать или исключать компоненты в зависимости от того, насколько часто вы предполагаете их использовать. Это означает, что установка по умолчанию, как правило, требует меньше места и происходит быстрее, чем выборочная установка. Кроме того, это означает, что многие компоненты, которые устанавливались в предыдущих версиях по умолчанию, в этой версии считаются настраиваемыми компонентами, которые требуется явно выбирать для установки.

 ![Диалоговое окно установки Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Настраиваемые компоненты включают Visual C++, Visual F#, SQL Server Data Tools, пакеты SDK и средства разработки кроссплатформенных мобильных приложений, а также сторонние пакеты SDK и расширения. Если вы не выбрали эти компоненты во время начальной установки, вы можете установить их позднее.

> [!NOTE]
>  Выборочная установка автоматически включает компоненты установки по умолчанию.

 Ниже приведен полный список настраиваемых компонентов.

|Наборы функций|Компоненты|
|------------------|----------------|
|**Обновления**|Visual Studio 2015 с обновлением 3|
|**Языки программирования**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Разработка для Windows и веб-разработка**|Средства публикации ClickOnce<br />LightSwitch<br />Инструменты разработчика Microsoft Office<br />Microsoft SQL Server Data Tools<br /> Веб-инструменты Майкрософт для разработчиков<br />Инструменты PowerShell для Visual Studio (сторонний)<br />Набор разработки для Silverlight<br />Средства разработки универсальных приложений Windows<br />Средства и пакеты SDK Windows 10<br />Средства Windows 8.1 и Windows Phone 8.0/8.1<br />Средства и пакеты SDK Windows 8.1|
|**Разработка кроссплатформенных мобильных приложений**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Разработка мобильных приложений Visual C++ для iOS и Android<br />Clang с Microsoft CodeGen|
|**Общие средства и пакеты средств разработки программного обеспечения**|Android Native Development Kit (сторонний)<br /> Пакет SDK для Android [сторонний]<br />API-интерфейсы для установки пакета SDK для Android (сторонний)<br />Apache Ant (сторонний)<br /> Java SE Development Kit (сторонний)<br /> Joyent Node.js (сторонний)|
|**Общие средства**|Git для Windows (сторонний)<br />Расширение GitHub для Visual Studio (сторонний)<br /> Средства расширения Visual Studio|

##  <a name="installing"></a> Установка Visual Studio
 Visual Studio можно установить с установочного диска DVD, с помощью службы подписки Visual Studio из [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) веб-сайта, загрузив веб-установщик из [Visual Studio Загружает](http://go.microsoft.com/fwlink/?LinkId=517106) веб-сайта, или путем создания макета автономной установки (см. в разделе [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) получить дополнительные сведения).

> [!IMPORTANT]
>  Установка [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]должна выполняться от имени учетной записи администратора. Тем не менее для работы с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] после установки они не нужны.

 Для установки всех компонентов Visual Studio учетной записи локального администратора необходимо предоставить следующие права.

|Отображаемое имя объекта локальной политики|Право пользователя|
|--------------------------------------|----------------|
|Резервное копирование файлов и каталогов|SeBackupPrivilege|
|Отладка программ|SeBackupPrivilege|
|Управление аудитом и журналом безопасности|SeSecurityPrivilege|

 Более подробную информацию о требованиях к учетной записи локального администратора см. в статье базы знаний [Установка SQL Server завершается ошибкой, если учетная запись для установки не имеет определенных прав пользователя](https://support.microsoft.com/en-us/kb/2000257).

###  <a name="BKMK_Media"></a> С помощью установочного носителя
 Чтобы установить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], в корневом каталоге установочного носителя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запустите файл установки для нужного выпуска:

|Выпуск|Файл установки|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

###  <a name="BKMK_Website"></a> Загрузка с веб-сайта продукта
 Посетите [загрузки Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106) страницы и выберите выпуск Visual Studio, который вы хотите.

### <a name="downloading-from-your-subscription-service"></a>Загрузка из службы подписки
 Посетите [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) страницы и выберите выпуск Visual Studio, который вы хотите.

###  <a name="BKMK_Offline"></a> Создание макета автономной установки
 Если у вас нет [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установочного носителя, или не иметь подписку Visual Studio, или вы не хотите установить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с помощью веб-установщик, можно выполнить «разъединенное» установки путем создания как автономную Макет установки. Дополнительные сведения см. в разделе [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) страницы.

##  <a name="enterprise"></a> Развертывание Visual Studio на предприятии
 Сведения о развертывании [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] по сети, см. в разделе [руководства администратора Visual Studio](../install/visual-studio-administrator-guide.md).

###  <a name="BKMK_Virtualized"></a> Установка Visual Studio в виртуализованной среде
 **Проблемы, связанные с видео, при использовании Hyper-V**

 В случае использования Windows Server 2008 R2 с Hyper-V и графическим ускорителем, система может работать медленнее, чем обычно.

 Дополнительные сведения см. в указанной ниже статье на веб-сайте корпорации Microsoft. [Видео может привести к снижению производительности с Windows Server 2008 и Windows Server 2008 R2 на основе включенной ролью Hyper-V и установленным ускорителем адаптера дисплея](http://go.microsoft.com/fwlink/?LinkID=231084).

 **Эмуляция устройств с помощью Hyper-V**

 При установке Visual Studio 2015 на реальном оборудовании без виртуализации можно выбрать компоненты, обеспечивающие эмуляцию устройств Windows и Android с помощью Hyper-V. При установке в Hyper-V эмуляция устройств Windows или Android недоступна. Это связано с тем, что эмуляторы являются виртуальными машинами сами по себе, а размещать одну виртуальную машину внутри другой на данный момент нельзя. Эту проблему можно решить, развернув и отладив приложение на реальном устройстве Windows или Android.

##  <a name="optionalComponents"></a> Установка дополнительных компонентов
 Если вы хотите установить компоненты, которые вы не были выбраны во время исходной установки, используйте следующую процедуру.

#### <a name="to-install-optional-components"></a>Чтобы установить дополнительные компоненты

1.  На странице **Программы и компоненты** **панели управления** выберите выпуск продукта, в который требуется добавить один или более компонентов, и нажмите кнопку **Изменить**.

2.  В мастере установки выберите **Изменить**, а затем выберите компоненты, которые необходимо установить.

3.  Нажмите кнопку **Далее**, а затем следуйте инструкциям.

##  <a name="helpContent"></a> Установка содержимого автономной справки
 После установки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]можно скачать дополнительное содержимое справки, чтобы сделать его доступным в автономном режиме.

#### <a name="to-install-or-uninstall-help-content"></a>Установка и удаление содержимого справки

1. В строке меню [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] выберите **Справка**, **Добавление и удаление содержимого справки**.

2. На вкладке **Управление содержимым** **средства просмотра справки (Майкрософт)** выберите источник установки для содержимого справки.

3. При поиске определенной коллекции справки введите ключевое слово или имя в текстовое поле **Поиск** и нажмите клавишу **ВВОД**.

4. Щелкните ссылку **Добавить** или **Удалить** рядом с именем нужной коллекции справки.

5. Нажмите кнопку **Обновить**.

   Дополнительные сведения о том, как установить или развернуть автономную справку, см. в разделе [руководство администратора средства просмотра справки](../ide/help-viewer-administrator-guide.md).

##  <a name="serviceReleases"></a> Проверка наличия исправлений и обновлений
 Visual Studio не обновляет расширения автоматически при обновлении с предыдущих версий, так как не все расширения совместимы. Необходимо переустановить расширения из [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) или от издателя программного обеспечения.

#### <a name="to-automatically-check-for-service-releases"></a>Автоматическая проверка наличия наборов исправлений

1.  В строке меню выберите **Сервис**, **Параметры**.

2.  В диалоговом окне **Параметры** раскройте элемент **Среда**, а затем выберите **Расширения и обновления**. Убедитесь, что установлен флажок **Автоматически проверять наличие обновлений** и нажмите кнопку **ОК**.

## <a name="registering-visual-studio"></a>Регистрация Visual Studio

1.  В строке меню выберите **Справка**, **О программе**.

     Диалоговое окно **О программе** содержит идентификационный номер продукта (PID). Для регистрации продукта необходимо указать PID и данные учетной записи Windows (например, адрес и пароль электронной почты на Hotmail или Outlook.com).

2.  В меню **Справка**выберите команду **Зарегистрировать продукт**.

##  <a name="repair"></a> Восстановление Visual Studio

#### <a name="to-repair-visual-studio"></a>Восстановление Visual Studio

1.  На странице **Программы и компоненты** **панели управления** выберите выпуск продукта, который необходимо восстановить, и нажмите кнопку **Изменить**.

2.  В мастере установки выберите **Восстановить**, нажмите кнопку **Далее**, а затем следуйте инструкциям.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Восстановление Visual Studio в автоматическом или в пассивном режиме (то есть для восстановления из источника)

1.  На компьютере, на котором установлена среда Visual Studio, откройте командную строку Windows.

2.  Введите следующие параметры:

     *DVDRoot* \\< файл установки\> \</quiet&#124;/passive > [/ norestart] / Repair

##  <a name="troubleshooting"></a> Устранение неполадок при установке
 Используйте следующие ресурсы, чтобы получить помощь в разрешении проблем настройки и установки:

-   Форум по[установке и настройке Visual Studio](http://go.microsoft.com/fwlink/?LinkID=151190) . Просмотрите вопросы и ответы от других пользователей сообщества Visual Studio. Если вы не нашли нужную информацию, задайте собственные вопросы.

-   Веб-сайт[службы поддержки Майкрософт для Visual Studio](http://go.microsoft.com/fwlink/?LinkID=251019) . Прочтите статьи базы знаний (KB) и узнайте, как связаться со службой поддержкой корпорации Майкрософт по вопросам установки Visual Studio.

##  <a name="relatedTopics"></a> Связанные разделы

|Заголовок|Описание|
|-----------|-----------------|
|[Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|В этой статье описывается установка Visual Studio, когда вы не подключены к Интернету.
|[Параллельная установка версий Visual Studio](../install/install-visual-studio-versions-side-by-side.md)|Сведения об установке и использовании нескольких версий Visual Studio на одном компьютере.|
|[Использование параметров командной строки для установки Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Список параметров командной строки, которые можно использовать при установке Visual Studio из командной строки.|
|[Удаление Visual Studio](../install/uninstall-visual-studio.md)|В этой статье описывается удаление Visual Studio.|
|[Руководство администратора Visual Studio](../install/visual-studio-administrator-guide.md)|Сведения о вариантах развертывания Visual Studio.|
|[Библиотека изображений Visual Studio](../designers/the-visual-studio-image-library.md)|Сведения об установке графики, которая может использоваться в приложениях Visual Studio.|
|[Начало разработки в Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Содержит сведения и ссылки, которые помогут вам более эффективно использовать Visual Studio.|

## <a name="see-also"></a>См. также

- [Вход в Visual Studio](../ide/signing-in-to-visual-studio.md)