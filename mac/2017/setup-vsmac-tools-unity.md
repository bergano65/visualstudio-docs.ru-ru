---
title: Настройка инструментов Visual Studio для Mac для Unity
description: Настройка и установка инструментов Unity для использования в Visual Studio для Mac
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: f423b77f8464b05b81be2ff7cdb08a2d8b007e0d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723066"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Настройка инструментов Visual Studio для Mac для Unity

Этот раздел описывает, как приступить к работе с инструментами Visual Studio для Mac для Unity.

## <a name="install-visual-studio-for-mac"></a>Установка Visual Studio для Mac

### <a name="unity-bundled-installation"></a>Пакетная установка Unity

Начиная с Unity 2018.1, Visual Studio для Mac является интегрированной средой разработки на C# по умолчанию для Unity и входит в помощник по загрузке Unity, а также в средство установки Unity Hub. Скачайте Unity с сайта [store.unity.com](https://store.unity.com/).

Во время установки убедитесь, что Visual Studio для Mac отмечена в списке компонентов для установки с Unity:

#### <a name="unity-hub"></a>Unity Hub

![установка unity hub](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Помощник по загрузке Unity

![установка помощника по загрузке Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Проверка обновления Visual Studio для Mac

В установку Unity может входить не последняя версия Visual Studio для Mac. Рекомендуется проверить наличие обновлений, чтобы использовать новейшие функции и инструменты.

* [Обновление Visual Studio для Mac](update.md)

### <a name="manual-installation"></a>Ручная установка

Если у вас уже есть Unity 5.6.1 или более поздней версии, но нет Visual Studio для Mac, можно установить Visual Studio для Mac вручную. Все выпуски Visual Studio для Mac включают инструменты Visual Studio для Mac для Unity, включая бесплатный выпуск Community:

* Скачайте Visual Studio для Mac с сайта [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Инструменты Visual Studio для Mac для Unity автоматически устанавливаются в процессе установки.
* Дополнительные сведения см. в указаниях из [руководства по установке](./installation.md?view=vsmac-2017&preserve-view=true).

> [!NOTE]
> Инструментам Visual Studio для Mac для Unity требуется компонент Unity версии 5.6.1 или более поздней. Чтобы убедиться, что инструменты Visual Studio Tools для Unity включены в вашей версии Unity, выберите **About Unity** (О программе Unity) в меню Unity и найдите текст "Microsoft Visual Studio Tools for Unity enabled" (Инструменты Microsoft Visual Studio для Unity включены) в левом нижнем углу диалогового окна.
>
> ![О программе Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Проверка того, что расширение инструментов Visual Studio для Mac для Unity включено

Хотя расширение инструментов Visual Studio для Mac для Unity должно быть включено по умолчанию, можно убедиться в этом, а также проверить номер установленной версии:

1. В меню Visual Studio выберите **Расширения...**

   ![Выберите "Расширения"](media/setup-vsmac-tools-unity-image1.png)

2. Разверните раздел "Разработка игр" и подтвердите наличие записи инструментов Visual Studio для Mac для Unity.

   ![Просмотр записи Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Настройка Unity для работы с Visual Studio для Mac

Начиная с Unity 2018.1 Visual Studio будет внешним редактором скриптов по умолчанию для Unity. Вы можете подтвердить или изменить внешний редактор скриптов на Visual Studio:

1. Выберите **Параметры...**  в меню Unity.

   ![Выберите "Параметры"](media/setup-vsmac-tools-unity-image4.png)

2. В диалоговом окне параметров откройте вкладку **Внешние инструменты**.

3. В раскрывающемся списке внешнего редактора скриптов выберите элемент **Visual Studio**, если он присутствует, в противном случае нажмите кнопку **Обзор...**

   ![Выберите Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Если вы нажали кнопку **Обзор...** , перейдите в каталог приложений, выберите Visual Studio и нажмите кнопку **Открыть**.

   ![Выберите "Открыть"](media/setup-vsmac-tools-unity-image6.png)

5. Выбрав Visual Studio в списке **External Script Editor** (Внешний редактор скриптов), закройте диалоговое окно параметров для завершения процесса настройки.