---
title: Приступая к работе с инструментами Visual Studio для Unity | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 6901c44e61ba291bbc40ad9654f27f52f0e7f48a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655179"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Начало работы с набором средств Visual Studio для Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе вы узнаете, как установить инструменты Visual Studio для Unity и настроить проект Unity для работы с Visual Studio.  
  
> [!IMPORTANT]
>  В Unity 5.2 добавлена встроенная поддержка инструментов Visual Studio для Unity 2.1, что упрощает настройку проекта. Для использования этой возможности потребуется Unity 5.2.0 или более поздней версии в Windows и инструменты Visual Studio для Unity 2.1 или более поздней версии.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для использования средств Visual Studio для Unity вам потребуется следующее:  
  
-   версия **Visual Studio** , поддерживающая расширение, например Visual Studio Community, Professional, Premium или Enterprise (скачать Visual Studio Community можно бесплатно);  
  
     [Скачать Visual Studio Community](http://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   **Unity** 4.0.0 или более поздней версии; **Unity** 5.2.0 или более поздней версии для использования встроенной поддержки инструментов Visual Studio для Unity 2.1 или более поздней версии.  
  
     [Скачать Unity](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Установка набора средств Visual Studio для Unity  
 Загрузите и установите набор средств Visual Studio для Unity из галереи Visual Studio. Необходимо установить нужный пакет для вашей версии Visual Studio. Для использования встроенной поддержки инструментов Visual Studio для Unity в Unity 5.2 или более поздней версии установите инструменты Visual Studio для Unity 2.1 или более поздней версии.  
  
-   Для Visual Studio 2015 Community, Visual Studio 2015 Professional или Visual Studio 2015 Enterprise  
  
     [Скачать инструменты Visual Studio 2015 для Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
-   Для Visual Studio 2013 Community, Visual Studio 2013 Professional или Visual Studio 2013 Premium  
  
     [Скачать инструменты Visual Studio 2013 для Unity](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
-   Для Visual Studio 2012 Professional или Visual Studio 2012 Premium  
  
     [Скачать инструменты Visual Studio 2012 для Unity](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
-   Для Visual Studio 2010 Professional или Visual Studio 2010 Premium  
  
     [Скачать инструменты Visual Studio 2010 для Unity](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
>  Версии Visual Studio Express не поддерживают расширения, такие как набор средств Visual Studio для Unity. Visual Studio 2013 Community — это бесплатная версия Visual Studio, которая поддерживает набор средств Visual Studio для Unity и другие расширения. Для большинства пользователей версия Visual Studio Community является более предпочтительной, чем версия Express.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Ваш первый проект Unity с набором средств Visual Studio для Unity  
 Теперь, когда у вас есть все необходимое, вы готовы к своему первому проекту Unity с Visual Studio. Настройка проекта Unity производится по-разному в зависимости от того, какие версии Unity и инструментов Visual Studio для Unity установлены. Выполните приведенные ниже инструкции для установленной версии Unity и инструментов Visual Studio для Unity.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5.2 или более поздней версии (требуются инструменты Visual Studio для Unity 2.1 или более поздней версии)  
 Начиная с версии Unity 5.2 больше не нужно импортировать пакет unitypackage инструментов Visual Studio в проекты. Если проект импортирует этот пакет unitypackage, Unity 5.2 игнорирует его и напрямую загружает инструменты Visual Studio для Unity из папки установки.  
  
#### <a name="1---create-a-unity-project"></a>1. Создание проекта Unity  
 Если у вас уже есть опыт работы с Unity, вы можете создать новый проект или загрузить один из собственных. Если вы загружаете проект, который импортировал пакет unitypackage инструментов Visual Studio для использования инструментов Visual Studio для Unity с предыдущей версией Unity, мы рекомендуем удалить его, удалив каталог UnityVS.  
  
 В противном случае, если у вас нет опыта работы с Unity, ознакомьтесь с базовым учебным пособием. На странице "Изучение Unity" найдите учебники с примерами проектов, с которых вы можете начать, а также с уроками, которые позволят вам создать собственную игру с помощью Unity. На данной странице имеются удобные учебники для нескольких различных игр.  
  
 [Учебники – страница "Изучение Unity"](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2. Настройка редактора Unity для использования набора средств Visual Studio для Unity  
 Чтобы в проекте можно было использовать инструменты Visual Studio для Unity, просто задайте Visual Studio в качестве внешнего редактора скриптов. В редакторе Unity в главном меню выберите пункт **Edit &gt; Preferences**(Правка &gt; Настройки), а затем в диалоговом окне **Unity Preferences** (Настройки Unity) выберите **External Tools**(Внешние средства). Далее укажите в качестве значения свойства **External Script Editor** (Внешний редактор скриптов) версию Visual Studio, которую нужно использовать (для этой версии Visual Studio должны быть установлены инструменты Visual Studio для Unity), и убедитесь в том, что задано свойство **Editor Attaching** (Присоединение редактора).  
  
 Чтобы проверить, включена ли встроенная поддержка инструментов Visual Studio для Unity, воспользуйтесь диалоговым окном **About Unity** (Сведения о Unity). In the Unity editor, on the main menu, choose **Help &gt; About Unity** (Справка &gt; Сведения о Unity). Если инструменты Visual Studio для Unity установлены и правильно настроены, в левом нижнем углу диалогового окна **About Unity** (Сведения о Unity).  
  
 Наконец, убедитесь в том, что вы установили целевой объект сборки на странице **Build Settings** (Параметры сборки) и что функция **Script Debugging** (Отладка скриптов) включена.  
  
 ![Настройка параметров сборки Unity для отладки.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3. Запуск Visual Studio из редактора Unity  
 Начиная с версии Unity 5.2 меню расширения **Инструменты Visual Studio** больше не требуется для запуска Visual Studio или настройки инструментов Visual Studio для Unity. Вместо этого после настройки Visual Studio в качестве внешнего редактора скриптов просто выберите файл скрипта в редакторе Unity, и ваш код откроется в Visual Studio.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Предыдущие версии Unity (до версии 5.2)  
 До версии Unity 5.2 встроенная поддержка инструментов Visual Studio для Unity отсутствовала. Поэтому для использования инструментов Visual Studio для Unity каждому проекту приходилось импортировать пакет unitypackage инструментов Visual Studio и настраивать другие параметры проекта.  
  
#### <a name="1---create-a-unity-project"></a>1. Создание проекта Unity  
 Если у вас уже есть опыт работы с Unity, вы можете создать новый проект или загрузить один из собственных. Если вы начинаете новый проект, импортируйте пакет unitypackage инструментов Visual Studio при его создании.  
  
 В противном случае, если у вас нет опыта работы с Unity, ознакомьтесь с базовым учебным пособием. На странице "Изучение Unity" найдите учебники с примерами проектов, с которых вы можете начать, а также с уроками, которые позволят вам создать собственную игру с помощью Unity. На данной странице имеются удобные учебники для нескольких различных игр.  
  
 [Учебники – страница "Изучение Unity"](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2. Настройка редактора Unity для использования набора средств Visual Studio для Unity  
 Если вы используете существующий проект Unity или не импортировали пакет unitypackage инструментов Visual Studio на этапе создания проекта, необходимо импортировать этот пакет. В редакторе Unity в главном меню выберите **Assets &gt; Import Package &gt; Visual Studio 2015 Tools** (Ресурсы &gt; Импорт пакета &gt; Набор средств Visual Studio 2015) (вы увидите вариант для версии Visual Studio, которую вы установили).  
  
 ![Импорт пакета VSTU в проект Unity.](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 Наконец, убедитесь в том, что вы установили целевой объект сборки на странице **Build Settings** (Параметры сборки) и что функция **Script Debugging** (Отладка скриптов) включена.  
  
 ![Настройка параметров сборки Unity для отладки.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3. Запуск Visual Studio из редактора Unity  
 Теперь необходимо запустить Visual Studio из Unity. При этом создается решение Visual Studio для вашего проекта, которое открывается в Visual Studio.  
  
 В редакторе Unity в главном меню выберите **"Средства Visual Studio", "Открыть в Visual Studio"**.  
  
 ![Открытие проекта Unity в Visual Studio.](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Следующие шаги  
 Сведения о работе с проектом Unity и его отладке в Visual Studio см. в разделе [Использование инструментов Visual Studio для Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>См. также  
 [Главная страница Unity](http://unity3d.com)
