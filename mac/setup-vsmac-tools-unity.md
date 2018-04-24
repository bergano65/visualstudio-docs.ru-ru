---
title: Настройка инструментов Visual Studio для Mac для Unity
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: a1d6d523de9a5a57cf6b4c696a68dbdde1428156
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Настройка инструментов Visual Studio для Mac для Unity

Этот раздел описывает, как приступить к работе с инструментами Visual Studio для Mac для Unity.

## <a name="install-visual-studio-for-mac"></a>Установка Visual Studio для Mac

Скачивание и установка Visual Studio для Mac. Все выпуски Visual Studio для Mac поддерживают инструменты Visual Studio для Mac для Unity, включая бесплатный выпуск Community:

* Скачайте Visual Studio для Mac с сайта [visualstudio.com](https://www.visualstudio.com/).
* Инструменты Visual Studio для Mac для Unity автоматически устанавливаются в процессе установки.
* Дополнительные сведения см. в указаниях из [руководства по установке](/visualstudio/mac/installation).

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Проверка того, что расширение инструментов Visual Studio для Mac для Unity включено

Хотя расширение инструментов Visual Studio для Mac для Unity должно быть включено по умолчанию, можно убедиться в этом, а также проверить номер установленной версии:

1.  В меню Visual Studio выберите **Расширения...**

  ![Выберите "Расширения"](media/setup-vsmac-tools-unity-image1.png)

2.  Разверните раздел "Разработка игр" и подтвердите наличие записи инструментов Visual Studio для Mac для Unity.

  ![Просмотр записи Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>Установка Unity

Инструментам Visual Studio для Mac для Unity требуется компонент Unity версии 5.6.1 или более поздней. С инструментами Visual Studio для Unity работают все планы Unity, включая бесплатный личный план. Скачайте Unity с сайта [store.unity.com](https://store.unity.com/).

> [!NOTE]
> Чтобы убедиться, что инструменты Visual Studio Tools для Unity включены в вашей версии Unity, выберите **About Unity** (О программе Unity) в меню Unity и найдите текст "Microsoft Visual Studio Tools for Unity enabled" (Инструменты Microsoft Visual Studio для Unity включены) в левом нижнем углу диалогового окна.
>
>   ![О программе Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Настройка Unity для работы с Visual Studio для Mac

Visual Studio нужно настроить в качестве внешнего редактора скриптов в Unity:

1.  Выберите **Параметры...**  в меню Unity.

  ![Выберите "Параметры"](media/setup-vsmac-tools-unity-image4.png)

2.  В диалоговом окне параметров откройте вкладку **Внешние инструменты**.

3.  В раскрывающемся списке внешнего редактора скриптов выберите элемент **Visual Studio**, если он присутствует, в противном случае нажмите кнопку **Обзор...**

  ![Выберите Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4.  Если вы нажали кнопку**Обзор...**, перейдите в каталог приложений, выберите Visual Studio и нажмите кнопку **Открыть**.

  ![Выберите "Открыть"](media/setup-vsmac-tools-unity-image6.png)

5.  Выбрав Visual Studio в списке **External Script Editor** (Внешний редактор скриптов), закройте диалоговое окно параметров для завершения процесса настройки.
