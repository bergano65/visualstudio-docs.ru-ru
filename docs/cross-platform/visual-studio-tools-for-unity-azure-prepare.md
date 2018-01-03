---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по подготовке в Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7554380435c77750eb48a5ce261cc0a2b3885ccd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="prepare-the-development-environment"></a>Подготовка среды разработки

Для использования пакета SDK Azure Mobile Client в Unity необходимо выполнить ряд предварительных требований.

## <a name="download-and-install-unity-2017"></a>Скачайте и установите Unity 2017

Требуется версия Unity 2017.1 или более поздняя. В этом пошаговом руководстве можно использовать все планы Unity, включая бесплатный личный план. Скачайте Unity с сайта https://store.unity.com/.

## <a name="download-and-install-visual-studio-2017"></a>Скачайте и установите Visual Studio 2017

Для этого пошагового руководства требуется Visual Studio 2017 15.3 или более поздней версии с рабочей нагрузкой "Разработка игр с помощью Unity". В пошаговом руководстве можно использовать любые выпуски Visual Studio 2017, включая бесплатный выпуск Community.

1. Скачайте Visual Studio 2017 на сайте https://www.visualstudio.com/.

2. Установите Visual Studio 2017 и убедитесь в том, что включена рабочая нагрузка **Разработка игр с помощью Unity**.

 ![Выбор рабочей нагрузки Unity](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Если среда Visual Studio 2017 уже установлена, просмотреть и изменить рабочие нагрузки можно, запустив Visual Studio Installer.

## <a name="create-a-new-3d-unity-project"></a>Создание проекта 3D Unity

Запустите Unity и создайте проект 3D.

![Создание проекта Unity](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>Выбор предварительной версии Visual Studio 2017 в качестве редактора скриптов

Возможно, среда Visual Studio 2017 уже настроена как внешний редактор скриптов Unity, но необходимо убедиться в том, что выбрана предварительная версия 15.3.

1. В меню **Edit** (Правка) Unity выберите пункты **Edit > Preferences...** (Изменить > Настройки...).

  ![Пункт меню "Preferences" (Настройки)](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Когда появится окно "Unity Preferences" (Настройки Unity), выберите слева вкладку **External Tools** (Внешние средства).

3. В раскрывающемся меню **External Script Editor** (Внешний редактор скриптов) выберите **Visual Studio 2017**.

  ![Выбор внешнего редактора скриптов](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Изменение среды выполнения скриптов Unity на .NET 4.6
Для использования в этом пошаговом руководстве пакета SDK Azure Mobile Client и его зависимостей требуется платформа .NET 4.6.

1. В меню **File** (Файл) в Unity выберите пункт **File > Build Settings...** (Файл > Параметры сборки...).

  ![Открытие параметров сборки](media/vstu_azure-prepare-dev-environment-image4.png)

2. Нажмите кнопку **Player Settings...** (Параметры проигрывателя...).

  ![Открытие параметров проигрывателя](media/vstu_azure-prepare-dev-environment-image5.png)

3. Параметры проигрывателя откроются в окне "Unity Inspector" (Инспектор Unity). В разделе **Configuration** (Конфигурация) откройте раскрывающийся список **Scripting Runtime Version** (Версия среды выполнения скриптов) и выберите пункт **Experimental (.NET 4.6 Equivalent)** (Экспериментальная (эквивалент .NET 4.6)). Появится диалоговое окно с запросом на перезапуск Unity. Нажмите кнопку **Restart** (Перезапуск).

  ![Выбор .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>Добавление ссылки на System.Net.Http.dll

Среда выполнения скриптов Unity, эквивалентная .NET 4.6, позволяет использовать пакет System.Net.Http, который необходим пакету SDK Azure Mobile Client. DLL-файл входит в состав Unity, однако для его использования необходимо добавить ссылку.

1. В окне "Project" (Проект) редактора Unity **щелкните правой кнопкой мыши** папку **Assets** (Активы) и выберите пункт **Show in Explorer** (Показать в проводнике).

  ![Отображение папки Assets в проводнике](media/vstu_azure-prepare-dev-environment-image7.png)

2. В появившемся окне проводника дважды щелкните каталог **Assets**, чтобы открыть его.

3. Внутри каталога Assets **щелкните правой кнопкой мыши** и выберите пункты **New > Text Document** (Создать > Текстовый документ).

4. Откройте новый текстовый документ в текстовом редакторе и добавьте следующую строку: `-r:System.Net.Http.dll`

5. Сохраните документ и закройте его.

4. Переименуйте новый текстовый документ в **mcs.rsp**, обязательно удалив расширение TXT.

  * Если расширения имен файлов скрыты, необходимо изменить параметры просмотра папок, чтобы отобразить их.
  * Откройте меню "Пуск" и выполните поиск по запросу "параметры папок". Выберите элемент **Параметры Проводника**.
  * Перейдите на вкладку **Вид** и в разделе дополнительных параметров снимите флажок **Скрывать расширения для зарегистрированных типов файлов**.

    ![Отображение папки Assets в проводнике](media/vstu_azure-prepare-dev-environment-image8.png)

После выполнения этих действий в корневом каталоге **Assets** проекта Unity должен быть файл с именем **mcs.rsp**, содержащий строку `r:System.Net.Http.dll`.

>[!NOTE]
> Для создания ссылок требуется версия инструментов Visual Studio для Unity 3.3 или более поздняя, которая входит в состав рабочей нагрузки Unity в Visual Studio 15.3 и более поздних версиях. Если выполнить эти действия не удается, убедитесь в том, что установлена правильная версия инструментов Visual Studio для Unity.

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Добавление пакета NuGet Newtonsoft.Json в проект

Для пакета SDK Azure Mobile Client требуется пакет Newtonsoft.Json. К сожалению, Unity не поддерживает пакеты NuGet. Если вы откроете проект Unity в Visual Studio и добавите пакет с помощью NuGet, пакет будет удален при следующем открытии проекта в редакторе Unity. Однако пакеты из NuGet можно добавлять в проект Unity вручную.

1. В каталоге Assets проекта Unity создайте папку с именем **NuGet Packages** (только для организаций).

2. Перейдите на страницу https://www.nuget.org/packages/Newtonsoft.Json/ и нажмите кнопку **Manual Download** (Скачать вручную). Скачайте файл NUPKG.

  ![Отображение папки Assets в проводнике](media/vstu_azure-prepare-dev-environment-image9.png)

3. Найдите скачанный файл и измените его расширение имени с NUPKG на **ZIP**. Это позволит просматривать и извлекать файлы из пакета, как из любого другого архива ZIP.

4. Откройте или извлеките каталог из ZIP-файла и перейдите в папку **\lib\net45**.

5. Скопируйте файл **Newtonsoft.Json.dll** в каталог **Assets\NuGet Packages** проекта Unity.

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Добавление пакета NuGet для SDK Azure Mobile Client в проект

Пакет SDK Azure Mobile Client содержит функции, упрощающие считывание данных из простых таблиц Azure и запись данных в них.

1. Перейдите на страницу https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/ и нажмите кнопку **Manual Download** (Скачать вручную). Скачайте файл NUPKG.

2. Найдите скачанный файл и измените его расширение имени с NUPKG на **ZIP**. Это позволит просматривать и извлекать файлы из пакета, как из любого другого архива ZIP.

3. Откройте или извлеките каталог из ZIP-файла и перейдите в папку **\lib\net45**.

4. Скопируйте файл **Microsoft.Azure.Mobile.Client.dll** в каталог **Assets\NuGet Packages** проекта Unity.

>[!WARNING]
> После выполнения этих действий обязательно перезапустите Unity и Visual Studio. В противном случае технология InteliSense может не распознать добавленные пакеты.

## <a name="conclusion"></a>Заключение

После выполнения этих действий проект Unity должен быть настроен для использования пакета SDK Azure Mobile Client. Вы можете протестировать среду разработки, создав скрипт C# в проекте Unity, открыв его в Visual Studio и введя следующие операторы using в начале скрипта:
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

Если технология IntelliSense обнаруживает эти операторы using, настройка выполнена правильно. Если возникают ошибки или технология IntelliSense не распознает пакеты, попробуйте перезапустить Unity и Visual Studio. Если и это не помогло, вернитесь к приведенным выше инструкциям.

## <a name="next-step"></a>Дальнейшие действия

* [Создание классов моделей данных](visual-studio-tools-for-unity-azure-data.md)
