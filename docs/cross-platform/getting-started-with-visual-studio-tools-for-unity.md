---
title: Приступая к работе с инструментами Visual Studio для Unity | Документы Майкрософт
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 9d924ee92258e348d5ffee1551fcde7707d711cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855213"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Начало работы с инструментами Visual Studio для Unity

## <a name="install-visual-studio"></a>Установка Visual Studio

### <a name="unity-bundled-installation"></a>Пакетная установка Unity

Начиная с Unity 2018.1, Visual Studio по умолчанию является редактором скриптов на C# для Unity и входит в помощник по загрузке Unity, а также в средство установки Unity Hub.

- Скачайте Unity с сайта [store.unity.com](https://store.unity.com/).

Во время установки убедитесь, что Visual Studio отмечена в списке компонентов, устанавливаемых с Unity:

#### <a name="unity-hub"></a>Unity Hub

![установка unity hub](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Помощник по загрузке Unity

![установка помощника по загрузке Unity](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Проверка обновления Visual Studio

Версия Visual Studio, которая входит в установку Unity, может не быть последней. Рекомендуется проверить наличие обновлений, чтобы использовать новейшие функции и инструменты.

- [Обновление Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Установка вручную

Если у вас уже установлен Visual Studio 2017 или вы предпочитаете выполнить установку вручную, запустите установщик Visual Studio.

1. [Загрузите установщик Visual Studio](/visualstudio/install/install-visual-studio) или запустите его (если он был ранее установлен).

1. Щелкните **Изменить** (если установлено) или **Установка** (для новой установки) для требуемой версии Visual Studio.

1. На вкладке **Рабочие нагрузки** прокрутите до раздела **Mobile & Gaming** (Мобильные приложения и игры) и выберите рабочую нагрузку **Game development with Unity** (Разработка игр с помощью Unity).

    ![Рабочая нагрузка Unity](media/vstu_unity-workload.png)

1. Щелкните **Изменить** (если установлено) или **Установка** (для новой установки) в правом нижнем углу окна установки.

## <a name="configure-unity-for-use-with-visual-studio"></a>Настройка Unity для работы с Visual Studio

Начиная с Unity 2018.1 Visual Studio будет внешним редактором скриптов по умолчанию для Unity. Вы можете подтвердить это или изменить внешний редактор скриптов на определенную версию Visual Studio.

1. Выберите **Параметры** в меню **Изменить**.

   ![Выберите "Параметры"](media/vstu_unity-preferences.png)

2. В диалоговом окне параметров откройте вкладку **Внешние инструменты**.

3. В раскрывающемся списке **внешнего редактора скриптов** выберите необходимую версию элемента Visual Studio, если она присутствует, в противном случае нажмите кнопку **Обзор...**.

   ![Выберите Visual Studio](media/vstu_unity-external-tools.png)

4. Если было выбрано **Обзор...**, необходимо перейти в каталог **Common7/IDE**, находящийся в каталоге установки Visual Studio, и выбрать файл **devenv.exe**. Затем щелкните **Открыть**.

   ![Выберите "Открыть"](media/vstu_browse-for-application.png)

5. После выбора Visual Studio из списка **внешнего редактора скриптов**, убедитесь, что флажок **Editor Attaching** (Присоединение редактора) установлен.

6. Чтобы завершить процесс настройки, закройте диалоговое окно **Параметры**.

## <a name="support-for-older-versions"></a>Поддержка устаревших версий

 Загрузите и установите Инструменты Visual Studio для Unity из Visual Studio Marketplace. Необходимо установить нужный пакет для вашей версии Visual Studio.

- Для Visual Studio 2015 Community, Visual Studio 2015 Professional или Visual Studio 2015 Enterprise

   [Скачать инструменты Visual Studio 2015 для Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Для инструментов Visual Studio для Unity требуется Unity версии не ниже чем 5.2, а также версия Visual Studio, поддерживающая расширения, например Visual Studio Community, Professional, Premium или Enterprise. Чтобы убедиться, что Инструменты Visual Studio для Unity включены в вашу версию Unity, выберите **About Unity** (О программе Unity) в меню **Справка** и найдите текст "Microsoft Visual Studio Tools for Unity enabled" (Инструменты Microsoft Visual Studio для Unity включены) в левом нижнем углу диалогового окна.
> ![О программе Unity](media/vstu_about-unity.png)

## <a name="next-steps"></a>Следующие шаги

 Сведения о работе с проектом Unity и его отладке в Visual Studio см. в статье [Инструменты Visual Studio для Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
